##  VPN
---

open beta for employes of IT departament.



#### Create User



```shell 

ssh -i ~/EC2-SP ec2-user@vpn.domain.com.br

cd /mnt/app 

./create-user.sh USERNAME

and send .ovpn file to user

```


#### Remove User

```
ssh -i ~/EC2-SP ec2-user@vpn.domain.com.br

cd /mnt/app 

./remove-user.sh USERNAME

```


#### Checking if Service stay Running

Execute <i>docker ps</i> command if openvpn container appears on return, everything is OK. For more information check the logs with <i>docker logs -f openvpn</i>

```shell

docker ps

[root@ip-172-44-1-204 scripts]# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                    NAMES
0d3deba0c13b        kylemanna/openvpn   "ovpn_run"          12 days ago         Up 12 days          0.0.0.0:1194->1194/udp   openvpn


```

Running Container:
```
docker run -d --memory=6g --cpus=3 -p 1194:1194/udp --privileged -e DEBUG=1  --name openvpn -v $OVPN_DATA:/etc/openvpn --log-driver=none kylemanna/openvpn
```
