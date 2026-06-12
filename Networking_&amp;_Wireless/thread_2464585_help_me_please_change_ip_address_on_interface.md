---
title: "help me please change ip address on interface"
date: 2021-07-05
forum: Networking &amp; Wireless
---

### Post by flatic on 2021-07-05
Hello.
I have server on ubuntu
```
lsb_release -dDescription:    Ubuntu 20.04 LTS

```
It was configured by another administrator, he has a static ip address
```
ifconfigeno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.1.0.164  netmask 255.255.255.0  broadcast 10.1.0.255
        inet6 fe80::26fb:a1de:52d3:874f  prefixlen 64  scopeid 0x20<link>
        ether a8:5e:45:55:a8:8e  txqueuelen 1000  (Ethernet)
        RX packets 506499  bytes 49964941 (49.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13346  bytes 1049918 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0x92f00000-92f20000

```
I need her ip address on 10.1.45.166/30 defautgateway 10.1.45.165
In files 
```
sudo cat /etc/netplan/01-network-manager-all.yaml# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```
in 
```
sudo cat /etc/network/if-if-down.d/      if-post-down.d/ if-pre-up.d/    if-up.d/
root@user-System-Product-Name:~# sudo cat /etc/network/if-

```
When me change 10.1.0.164 on 10.1.45.166 ?
I configuration  sudo cat /etc/netplan/01-network-manager-all.yaml```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno0:
      addresses:
        - 10.1.45.166/30
      gateway4: 10.1.45.165
      nameservers:
          addresses: [10.1.0.203, 10.1.0.204]
```
but when me delete ip 10.1.0.164 ?
Help me please.

---

### Post by chili555 on 2021-07-05
I suggest that you return the netplan yaml file to its default and set the static IP in Network Manager:

[IMG]https://linuxconfig.org/images/04-set-configure-static-ip-address-ubuntu-18.04-bionic-linux.png[/IMG]

Of course, substitute your details here.

Restart NM:

```
sudo service NetworkManager restart

```
Confirm that you have the address requested:

```
ip addr show
```

---

