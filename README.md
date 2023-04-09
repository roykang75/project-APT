# project-APT
APT Project

## eureka
``` bash
http://localhost:8761/
```

## zipkin
```bash
http://localhost:9411/
```


## logging with elasticsearch
```bash
## docker network 생성
$ docker network create elastic-logging

## es 생성
$ docker run -d --name es-logging --net elastic-logging -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.10.2

## kibana 생성
## docker run -d --name kibana-logging --net elastic-logging -p 5601:5601 -e ELASTICSEARCH_HOSTS=http://<es-host-address>:9200 docker.elastic.co/kibana/kibana:7.10.2
$ docker run -d --name kibana-logging --net elastic-logging -p 5601:5601 -e ELASTICSEARCH_HOSTS=http://192.168.1.76:9200 docker.elastic.co/kibana/kibana:7.10.2
```



## zipkin with elasticsearch
```bash
## docker network 생성
$ docker network create elastic-zipkin

## es 생성
$ docker run -d --name es-zipkin --net elastic-zipkin -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.10.2

## kibana 생성
## docker run -d --name kibana-zipkin --net elastic-zipkin -p 5601:5601 -e ELASTICSEARCH_HOSTS=http://<es-host-address>:9200 docker.elastic.co/kibana/kibana:7.10.2
$ docker run -d --name kibana-zipkin --net elastic-zipkin -p 5601:5601 -e ELASTICSEARCH_HOSTS=http://192.168.1.76:9200 docker.elastic.co/kibana/kibana:7.10.2

## zipkin 생성
## docker run -d --name zipkin --net elastic-zipkin -p 9411:9411 --env STORAGE_TYPE=elasticsearch --env ES_HOSTS=http://<es-host-address>:9200 openzipkin/zipkin
$ docker run -d --name zipkin --net elastic-zipkin -p 9411:9411 --env STORAGE_TYPE=elasticsearch --env ES_HOSTS=http://192.168.1.76:9200 openzipkin/zipkin
```
