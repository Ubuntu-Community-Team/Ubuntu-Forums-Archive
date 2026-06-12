---
title: "proper interfaces setup?"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by Higgins909 on 2014-09-19
I am trying to narrow down why my proxy server has stopped working with streaming videos on youtube and facebook, and also some loading issues with youtube facebook and google.

interface:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface


#LAN
auto eth0
iface eth0 inet static
address 192.168.0.99
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8
#8.8.4.4

```
I have a static ip setup, and put dns in there, but how would I add 8.8.4.4 as a secondary?
i've tried removing dns by #ing it out and that loses google pinging(is that supposed to happen?)

for squid 3 I even tried turing off all refresh_pattern and still ran into loading issues

The main question is how to properly setup the interface file.

Thanks,
Higgins909

---

### Post by Hadaka on 2014-09-19
Perhaps this will help,,
[http://ubuntuforums.org/showthread.php?t=2230898](http://ubuntuforums.org/showthread.php?t=2230898)

---

