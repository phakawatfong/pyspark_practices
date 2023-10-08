# Project to practice setup Apache Spark on local using Docker

ref:
- https://medium.com/@SaphE/testing-apache-spark-locally-docker-compose-and-kubernetes-deployment-94d35a54f222

## prepare docker environment configuration
mkdir docker-compose-way
touch /docker-compose-way/Dockerfile
touch /docker-compose-way/start-spark.sh

cd /docker-compose-way

## Build docker image and name it `our-own-apache-spark:3.4.0`
`docker build -t our-own-apache-spark:3.4.0 .`

## See docker-image summary
`docker scount quickview`

## Run Spark with docker-compose
`docker compose up`

## Spark-Master WebUI
http://localhost:9090/

## Get into Spark-Cluster Container
`docker exec -it <container_name_of_spark_master_node> sh`

## Run Spark-job example
`cd /bin`
`./spark-submit --master spark://0.0.0.0:7077 --name spark-pi --class org.apache.spark.examples.SparkPi  local:///opt/spark/examples/jars/spark-examples_2.12-3.4.0.jar 100`