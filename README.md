#### pkmasdocker

- cp3
```
docker-machine create --driver vmwarefusion registry
docker-machine env registry
```

<??>
- cp4
execute command in docker container without the need to connect
```
docker exec -d  //daemon
docker exec -i  //interactive
docker top name
```



- cp6
docker machine
install.using curl  
```
curl -L https://github.com/docker/machine/releases/download/v0.4.0/docker-machine_linux-amd64 > /usr/local/bin/docker-machine
chmod +x /usr/local/bin/docker-machine
```

create a driver
```
docker-machine create --driver virtualbox <name>
```
using ec2
```
docker-machine create --driver amazonec2 --amazonec2-access-key <aws_access_key> --amazonec2-secret-key <aws_secret_key> --amazonec2-vpc-id <vpc_id> --amazonec2-subnet-id <subnet_id> --amazonec2-zone <zone> <name>
```





- cp8
install swarm
```
docker pull swarm
```
Three components of Docker Swarm  
Swarm, Swarm manager, Swarm host  


create a swarm token first:
```
docker run --rm swarm create
```

create swarm manager:
```
docker-machine create -d virtualbox --swarm --swarm-master --swarm-discovery token://12345 swarm-master
docker-machine ls
```

```
docker-machine env swarm-master    
eval "$(docker-machine env swarm-master)"
```

Joining nodes

```
docker-machine create -d virtualbox --swarm --swarm-discovery token://12345 swarm-node1
docker-machine ls
docker run --rm swarm list token://12345
```


check docker env for each node
```
docker-machine env swarm-node1
```

get info/get ps
```
docker -H tcp://192.168.99.103:2376 info
```




