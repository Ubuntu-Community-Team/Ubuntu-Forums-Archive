---
title: "nmap says: 111/tcp  open  rpcbind is open"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by charming-butcher on 2007-01-05
root@idea:/home nmap a.host

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-01-05 15:47 CET
Interesting ports on a.host:
Not shown: 1692 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
**111/tcp  open  rpcbind**
819/tcp  open  unknown
2049/tcp open  nfs

...I know the meaning of other ports and why they are open but what is rpcbind? Why is it running? I have not found any appropriate daemon in init.d to shut it down. After removing these pkgs

```
apt-get --purge remove rpc2-tools liblua5.1-0 librpc2-4 
```

the port remained open. **How can I close this port (not by a firewall)?**

---

### Post by play0r on 2007-01-05
> 111/tcp open rpcbind

i believe this is connected to portmapper, if you don't need it uninstall it.

ez,
play0r

---

### Post by charming-butcher on 2007-01-05
```
/etc/init.d/portmap stop
```

Yep, this was the portmap daemon. Thanks!

---

