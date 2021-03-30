# Github actions runner on Docker for Organizations

Create your own docker image to run your own self-hosted github actions.

Heads up, You will need an organization.

## Instructions

1. Clone this repo

    ```bash
    git clone git@github.com:obg-lab/action-runner-org-docker
    ```

1. Build the docker image

    ```bash
    cd action-runner-org-docker
    docker build -t github-actions-runner .
    ```

1. Run the container

    To run the container you will need to fill some environment variables.

    | ENV VAR      | Description                                                                               | Default Value       |
    | ------------ | ----------------------------------------------------------------------------------------- | ------------------- |
    | ORGANIZATION | The identification of your organization (obg-lab in my case)                              | (empty)             |
    | ACCESS_TOKEN | Your personal access token. You can create one [here](https://github.com/settings/tokens) | (empty)             |
    | RUNNER_NAME  | The name of your runner                                                                   | docker-runner       |
    | LABELS       | Labels of your runner                                                                     | self-hosted, docker |

    Run the runner:

    **Docker**

    ```bash
    docker run -it github-actions-runner -e ORGANIZATION [your-organization] -e ACCESS_TOKEN [your-token]
    ```

    **Docker Compose**

    Or update the `docker-compose.yml` environments section and run like this:

    ```bash
    docker-compose up --build
    ```

    The log output will looks like this. When you see `Listening for Jobs` log it means your runner is ready and you also can see it on actions page in your organization.

    ![Console log](docs/console.png)

## Next steps

- deploy it to docker hub
- traduzir readme para português (pt-BR)
- alterar para funcionar com contas não organizações
- adicionar fund
