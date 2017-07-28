# Execute query on database and export to csv

## Run in docker

    docker-compose up -d database
    docker-compose run db2csv \
            db2csv \
            -debug \
            -server database \
            -user  demo  \
            -password  insecure \
            -database postgres \
            -port 5432 \
            -query "SELECT 1,2,3,4 as DEMO;"

    cat /tmp/export/output.csv

## Development: 'go' runtime in docker, editing in IDE

    # Mount the source folders into the docker.

    docker-compose up -d database
    docker-compose build db2csv
    docker-compose run -v "${PWD}:/go/src/db2csv" -v"/tmp/export:/tmp/export" db2csv bash


    db2csv \
          -debug \
          -server database\
          -user  demo  \
          -password  insecure \
          -database postgres \
          -port 5432 \
          -query "SELECT 1,2,3,4 as DEMO;"

    cat /tmp/export/output.csv
