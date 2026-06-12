---
title: "How to make iptables rules persistant?"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by jsacksteder on 2007-03-25
If I add iptables rules manually, how do I get those to survive a reboot? Do I need to invoke iptables-save and send that to a file somewhere? Does it happen automatically? 

I can't find any references to iptables in any of the init scripts.

---

### Post by stuntgp2000 on 2007-03-25
Hi, I have no good understanding of Linux run levels but I managed to get iptables loading automatically using a script.

what I do is write all firewall rules into a file named iptables which I copy into /etc/init.d/
then 
```
sudo update-rc.d iptables start 99 2 . stop 00 2 0 1 6 .
```

I hope I helped

---

### Post by johnc4510 on 2007-03-25
Firestarter is the Graphical front end for iptables. This will save all preferences and run at boot.

---

### Post by jsacksteder on 2007-03-28
This document had the least-bad solution. 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

