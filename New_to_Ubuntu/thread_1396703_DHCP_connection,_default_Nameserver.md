---
title: "DHCP connection, default Nameserver"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by ICEB3AR on 2010-02-02
Hi there,

is it possible, if i have a connection eth0 which uses DHCP to get the Network Information and running a DNS-Server on the same computer to say That the DNS-Server on the local machine should be used. The Problem is that the resolv.conf is gonna be overwritten on restarting network because of using DHCP.

Thanks to all replies.

---

### Post by skatinjj on 2010-02-02
> **ICEB3AR said:**
> Hi there,

is it possible, if i have a connection eth0 which uses DHCP to get the Network Information and running a DNS-Server on the same computer to say That the DNS-Server on the local machine should be used. The Problem is that the resolv.conf is gonna be overwritten on restarting network because of using DHCP.

Thanks to all replies.

It might work not sure haven't tried it before, but I'm sure it would work much better with 2 NICs for separate IP addresses.

---

### Post by ICEB3AR on 2010-02-02
Don't know if you understand me right.
The Problem is, that if i put in the resolv.conf the localhost-address as the nameserver this should work, but on restarting the network the resolv.conf will be overwritten with the wrong nameserver. Is there a way where i can say that it should get all information from dhcp, but uses 127.0.0.1 as nameserver. I cannot change the dhcp-server which is serving the nic (eth0), which is the main problem. If this wouldn't be i would use a static connection.

I have 3 NIC, but i need them for other things.

---

### Post by Iowan on 2010-02-02
There are a couple of options in */etc/dhcp3/dhclient.conf* re: nameservers - one is **prepend** which puts your preferred nameserver first on the list - another is **supercede** which:> 
       If for some option the client should always use a locally-configured value  or  values rather than whatever is supplied by the server, these values can be defined in the supersede statement.


---

### Post by ICEB3AR on 2010-02-03
Okay thanks for your answer I'll give it a chance :)

---

