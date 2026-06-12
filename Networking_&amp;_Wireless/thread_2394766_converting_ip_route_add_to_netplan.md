---
title: "converting ip route add to netplan"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by arya6000 on 2018-06-20
I also asked this on askubuntu, but no answer so far, so I thought I would try here too

I'm following an answer I found on Serverfault located here [https://serverfault.com/a/487911/141509](https://serverfault.com/a/487911/141509), but it uses "ip route" which is not persistent. But I did work and it does work. Now I'm trying to make it persistent by adding it to my netplan file


I created the following routing table in rt_table

```
10 wlx74da388c32c7
```
Below is my full rt_table

```
#
# reserved values
#
255 local
254 main
253 default
0   unspec
#
# local
#
#1  inr.ruhep
10 wlx74da388c32c7
```

I'm trying to convert my ip route add and ip rule add commands to my netplan. Below are the two commands.

```

ip route add default via 172.16.11.254 table wlx74da388c32c7
ip rule add from 172.16.11.107 lookup wlx74da388c32c7

```
172.16.11.107 is the ip address and 172.16.11.254 is the gateway address. Below is what I have now, but I do know that it's wrong

```
network:
    ethernets:
        enp1s0:
            addresses:
            - 192.168.1.212/24
            gateway4: 192.168.1.1
            nameservers:
                addresses:
                - 8.8.8.8
                - 8.8.4.4
                search: []
            optional: true
    wifis:
        wlx74da388c32c7:
            dhcp4: true
            access-points:
                "home":
                    password: "mypassword"
            routes:
                - to: 172.16.11.0/24
                  via: 172.16.11.254
                  table: 10
            routing-policy:
                - from: 172.16.11.0/24
                  table: 10
    version: 2
```

---

