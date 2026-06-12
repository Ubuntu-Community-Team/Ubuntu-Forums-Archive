---
title: "Wi-Fi disabled on HP550, Network Controller Intel PRO/Wireless 3945ABG"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by Prateek_Ropia on 2014-02-24
Hello All,

I upgraded to Ubuntu 13.10 from 12.04. Everything works fine but for the Wi-fi. 
Ubuntu has disabled my wifi so strongly(is that a way to say it?), that my wifi doesn't even work on Windows 7(installed on a other partition)

I tried many solutions posted here on this forum for this problem, but none of them work.

Here is some information about my system that I have been able to get:

```
rfkill list all
2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

```
lspci -nnk | grep -A2 0280
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:135b]
    Kernel driver in use: iwl3945
```

Any help would be much appreciated guys! :o

Thanks.

---

### Post by wildmanne39 on 2014-02-24
Hi, it looks like your wireless is turned off, if it has a switch push or slide it once and see if it comes on if not it will be a key combination like fn + f5.
Thanks

---

