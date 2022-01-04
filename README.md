# schemaspy-kit
This allows you to try [`SchemaSpy`](https://github.com/schemaspy/schemaspy) immediately with docker-compose.schemaspy

## Usage

1. Clone the repository.

```
git clone https://github.com/soartec-lab/schemaspy-kit.git
```

2. Define `network` in　`docker-compose` so that it connects to the db that is already running.

The `docker-compose` already has a `network` definition in the comments, so comment it out and change the `sample_network` to your network.

```yaml
# networks:
    #   - sample_network
# networks:
#   sample_network:
#     external: true
```

3. Define environment variables.

Copy `.env.sample` to define the environment variables.

```bash
$ cat .env.sample

DB_DATABASE_NAME=localhost
DB_USER_NAME=root
DB_PASSWORD=password
DB_HOST=db
DB_PORT=3306

$ cp .env.sample .env
```

`.env` is specified in the　`env_file` property of `docker-compose`.

TIP: Environment variables can also be specified individually in the `environment` definition instead of　`env_file` in `docker-compose`.


4. Run docker-compose

When you start `docker-compose`, it does the following:

1. Analyze the DB information with `schemaspy` and output the static page file to the `output` directory.

2. Host the `output` directory output by schemaspy with `nginx` on port`8088`.

```bash
$ docker-compose up
```

5. Visit `localhost:8088`.

Displayed index page by `schemaspy`.
