---
title: "Error in network definition //etc/netplan/50-cloud-init.yaml expected mapping"
date: 2018-06-18
forum: Networking &amp; Wireless
---

### Post by arya6000 on 2018-06-18
I have added the wifi section to my netplan


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
                "FiOS-GIH0V":
                    password:"mypassword"
    version: 2
```


however when I run netplan generate

I get the following 

```
Error in network definition //etc/netplan/50-cloud-init.yaml line 22 column 20: expected mapping
```


which is on this line


```
                "FiOS-GIH0V":
```


And column 20 would be on the "O" of FiOS


I can't figure out what I did wrong here.

---

