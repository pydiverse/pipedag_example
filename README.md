# Example code for pydiverse pipedag

## Installation / Activation

```bash
conda env create
conda activate pipedag_example
```

or

```bash
mamba env create
conda activate pipedag_example
```

or

```bash
pip install pydiverse-pipedag docker-compose psycopg2-binary kazoo
```

or

```bash
python -m venv pipedag_example
source pipedag_example/bin/activate
pip install pydiverse-pipedag docker-compose psycopg2-binary kazoo
```

## Running test code

```bash
docker-compose up
```

and in another terminal

```bash
export POSTGRES_USERNAME=sa
export POSTGRES_PASSWORD=Pydiverse23
python run_pipeline.py
```

Finally, you may connect to your localhost postgres database `pipedag_default` and
look at tables in schemas `stage_1`..`stage_3`.

If you don't have a SQL UI at hand, you may use `psql` command line tool inside the docker container.
Check out the `NAMES` column in `docker ps` output. If the name of your postgres container is
`pipedag_example_postgres_1`, then you can look at output tables like this:

```bash
docker exec pipedag_example_postgres_1 psql --username=sa --dbname=pipedag_default -c 'select * from stage_1.dfa;'
```

Or more interactively:

```bash
docker exec -t -i pipedag_example_postgres_1 bash
psql --username=sa --dbname=pipedag_default
\dt stage_*.*
select * from stage_2.task_2_out;
```
