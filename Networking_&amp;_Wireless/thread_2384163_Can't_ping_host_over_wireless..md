---
title: "Can't ping host over wireless."
date: 2018-02-03
forum: Networking &amp; Wireless
---

### Post by publicface on 2018-02-03
Three issues.
 1) 2 PCs.  Hostnames yellow running ubuntu 16.04 and blue running kubuntu 16.04.  Each can ping the other over Ethernet, but not wireless.

 2) Can’t wireless print

 3) FQDN resolves locally but not with 8.8.8.8 as the server; i.e. externally, although a testing site is able to connect to yellow w/out problem.  

Thank you in advance.

---

### Post by Kirboosy on 2018-02-03
1. Do you have any VLAN separation on your network between wireless and wired?
2. See 1
3. Avahi is a service designed to help with this issue. Its installed by default on Ubuntu. You can check to make sure the service is running 
```
systemctl status avahi-daemon.service
```
Basic use is <hostname>.local
```
ping yellow.local
```
```
ping blue.local
```

You can also use it to scan and find various hosts on your network
```
avahi-browse -alr
```

---

