---
title: "Virtual Interfaces"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by lukeqsee on 2008-08-22
I need to setup up a network with my ethernet NIC having two connections: 
eth0 and eth0:1

I want to use static ips, but my router assigns static by MAC address, how do I give them different MAC addresses?

Thanks, 
Luke

---

### Post by spd106 on 2008-08-23
I don't really think you should be altering the MAC addresses unless you really have to. Depending on driver support you could try ifconfig or failing that install macchanger and use that instead.

---

### Post by matt79 on 2008-08-23
> **lukeqsee said:**
> I need to setup up a network with my ethernet NIC having two connections: 
eth0 and eth0:1

I want to use static ips, but my router assigns static by MAC address, how do I give them different MAC addresses?

Thanks, 
Luke


You can not set the MAC address. They are unique and assigned by the company that makes the network cards. Do you have any problem accessing the network from one network card?

---

