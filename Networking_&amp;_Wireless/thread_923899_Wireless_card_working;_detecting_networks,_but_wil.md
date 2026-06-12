---
title: "Wireless card working; detecting networks, but will not connect"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by jsnare01 on 2008-09-18
Okay, I just fixed my wireless connection with madwifi, and so now my wireless card works, but when I try to connect to my router, it will not connect. It can detect the network, but it won't connect. Help?

---

### Post by jsnare01 on 2008-09-19
bump

---

### Post by jsnare01 on 2008-09-19
Scratch that--it isn't even detecting networks anymore.

---

### Post by lswest on 2008-09-19
can you post the output of the following commands:
```
lshw -C network
lspci
iwconfig
ifconfig
iwlist scan
``` (each one in seperate code or quote boxes would be nice).  Maybe we can sort this out.

---

### Post by jsnare01 on 2008-09-19
Strange. It just started working all of a sudden. I'm using it now. Thanks anyway.

---

### Post by lswest on 2008-09-19
> **jsnare01 said:**
> Strange. It just started working all of a sudden. I'm using it now. Thanks anyway.

Haha, I have that affect on wireless cards :P  A few of my friends get pissed at me cuz their wireless works when just come near me (often because they intend to ask me to fix it...which...I do, I guess :P)  Anyways, if it stops connecting, try disabling ipv6 in your /etc/modprobe.d/aliases file (the last line will say ipv6 at the end, change ipv6 to off, and leave yourself a comment if you want to remember).

---

### Post by flame0086 on 2008-09-19
I had the same problem as the original poster today. Have a broadcom wireless and everything was working fine. Turned the laptop off, then back on, saw the wireless network but it would not connect.

> **lswest said:**
> Haha, I have that affect on wireless cards :P  A few of my friends get pissed at me cuz their wireless works when just come near me (often because they intend to ask me to fix it...which...I do, I guess :P)  Anyways, if it stops connecting, try disabling ipv6 in your /etc/modprobe.d/aliases file (the last line will say ipv6 at the end, change ipv6 to off, and leave yourself a comment if you want to remember).

This seemed to resolve the issue for me, but only after I restarted my laptop.

---

### Post by lswest on 2008-09-20
> **flame0086 said:**
> I had the same problem as the original poster today. Have a broadcom wireless and everything was working fine. Turned the laptop off, then back on, saw the wireless network but it would not connect.



This seemed to resolve the issue for me, but only after I restarted my laptop.

Yeah, I had the issue using the new wl driver in intrepid, since it was searching for ipv6 routers, and not finding any.  Don't ask me why.

---

