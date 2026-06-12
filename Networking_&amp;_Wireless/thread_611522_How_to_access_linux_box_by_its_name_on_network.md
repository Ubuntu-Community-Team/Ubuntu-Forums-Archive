---
title: "How to access linux box by its name on network"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by bjorntheart on 2007-11-13
I have a ubuntu feisty desktop with mysql5 installed on a machine, that wil be a small company's database server.

I need to access this machine from windows and linux PCs on a network through the name of the linux box and not the IP address. 

Are there any configuration I need to look at or will it automatically be setup like this after I get the computer setup on the network

Thanx

---

### Post by bjorntheart on 2007-11-13
Ok. I've managed to come up with a solution, but this is not the desired solution I'm looking for

I've edited my.cnf file and added 
```
bind-address 0.0.0.0
```

I know this allows for all ip address, but how else I'm going to control the windows PCs setup up with dynamic IP addresses (If I got this right??)

I also edited the windows host file and added this line 
```
192.168.1.11                  ccdimysqlserver 
```    

Now, I still have a problem. I don't have access to all the windows machines on the network to change all the host files, and if I had access, what if there were a 150 users? Do you think I'm going around 150 workstations changing all the host files......I don't think so!!!

Any help welcome all you pros out there

cia

---

