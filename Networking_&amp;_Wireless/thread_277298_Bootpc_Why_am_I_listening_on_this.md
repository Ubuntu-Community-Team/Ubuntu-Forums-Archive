---
title: "Bootpc? Why am I listening on this?"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by dguido on 2006-10-14
Why is my ubuntu box listing on the bootpc port?  Do I need this, and how do I shut it off?

---

### Post by dguido on 2006-11-22
anyone know?  this is really bugging me.  I want my Ubuntu box to be secure and not listen on a handful of ports I don't care about, I'd rather it be ssh and nothing else.

---

### Post by rscheideman on 2006-11-22
How do you know it is listening on the bootpc port?

---

### Post by dguido on 2006-11-22
netstat -la
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State         
tcp        0      0 *:ssh                   *:*                     LISTEN         
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:smtp          *:*                     LISTEN              
udp        0      0 *:bootpc                *:*                                       
raw        0      0 *:icmp                  *:*                     7

That * should mean it's listening for connections from anywhere right?

---

### Post by Azalin on 2006-11-23
Usually this means you have a service running that listens for this, maybe check synaptics packetmanager to see if you have anything installed that refers to bootpc...

---

### Post by kaaposc on 2008-04-01
> **dguido said:**
> anyone know?  this is really bugging me.  I want my Ubuntu box to be secure and not listen on a handful of ports I don't care about, I'd rather it be ssh and nothing else.

in case if anyone still interested, doing ```
sudo netstat -ap
``` gives more info about bootpc port - dhclient3 is listening on it. more about dhclient read manpages.

---

