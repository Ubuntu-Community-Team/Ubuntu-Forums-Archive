---
title: "Adding Route, Lost Connection"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by kwN7kft on 2014-05-10
Hi there,

Tried to add route to a remote ubunut server and lost connection
Is there anyway to revert it ?

Source :
Ubuntu Server 12.04
192.168.1.10

Destination 
Ubuntu server 12.04
10.0.10.1

I the add the following command on source

route add 10.0.10.1/32 eth0

Lost ssh connection and the machine access, is there anywway to rever it ?

Thanks to all.

---

### Post by kwN7kft on 2014-05-11
Anyone to Help ?

---

### Post by spynappels on 2014-05-11
You're going to have to give a bit more information.

For example:

What sort of network setup do you have, is the server you're trying to access at work and you're traversing the internet, or is it a separate subnet with a gateway on the 192.168.1.x subnet?

What is the output of 

```
ip route show
```

and 

```
ip address show
```

---

