---
title: "Zeroconf/Avahi issues"
date: 2020-07-26
forum: Networking &amp; Wireless
---

### Post by jadechessink on 2020-07-26
recently added avahi to my home computers and for a while i was able to ping other computers using their name.local, then i had to wipe/re-install and i cant get it to work anymore and my host name seems to have changed on nmap to something weird. any insight would be greatly appreciated. 

```
hostnamectl
   Static hostname: dragon
         Icon name: computer-desktop
           Chassis: desktop
        Machine ID: 47d7a10c594843ddbfaa9d8cf345f7cd
           Boot ID: df4f797141f94062a9e275c510c1c0db
  Operating System: Ubuntu 18.04.4 LTS
            Kernel: Linux 4.15.0-112-generic
      Architecture: x86-64


cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    dragon
192.168.1.223     omv

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


cat /etc/resolv.conf
nameserver 127.0.0.53
options edns0
search local

cat /etc/nsswitch.conf
passwd:         compat systemd
group:          compat systemd
shadow:         compat
gshadow:        files

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

### Post by wildmanne39 on 2020-07-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

