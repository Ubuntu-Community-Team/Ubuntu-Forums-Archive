---
title: "Default Active Network Connections is not eth0, why?"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by jiapei100 on 2015-03-24
Hi, all:

I've got 3 network card port, one for Internet, the other two for some Network Devices. However, right after all three ports are plugged in, the Internet stopped working:

On the top-right corner of Ubuntu, ```
Network Icon->Connection Information->Active Network Connections
```, that shows my Network Connection Status, **default **is automatically changed to **eth1**, instead of **eth0** .

I found some interesting symptoms:
[LIST=1]
[*]In only the port for Internet is connected, but disconnect the connections for the other 2 devices, I can browse the Internet --- certainly, the **default **is **eth0**.
[*]In any 2 out of 3 connections are connected, it looks like the **default **network port is the **latter **one which is connected ( network ports connect to my computer sequentially, namely, in a row but not simultaneously.)
[*]In 3 ports are all connected, there seems to be **NO **reasonable rules to decide which will be chosen as the **default **port. It's clearly **arbitrary**.
[/LIST]

Isn't there a simple way or a **command line** for me to change/**set **the **default **network port is **eth0 **???


Thank you 
Pei

---

### Post by ian-weisser on 2015-03-25
> **jiapei100 said:**
> Isn't there a simple way or a **command line** for me to change/**set **the **default **network port is **eth0 **???

See /etc/udev/rules.d/70-persistent-net.rules !!!

---

### Post by SeijiSensei on 2015-03-25
If the interfaces are configured with static IPs in /etc/network/interfaces, the one that has the "gateway" directive will be used for upstream communications.

---

