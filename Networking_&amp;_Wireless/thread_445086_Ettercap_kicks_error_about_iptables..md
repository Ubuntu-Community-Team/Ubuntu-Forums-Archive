---
title: "Ettercap kicks error about iptables."
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by acidblue on 2007-05-15
Whenever i run 'ettercap -G' i notice it kicks an error in the terminal window:

iptables v1.3.6: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
 Ettercap seems to run fine, it's just that this error surprises me.
Any ideas??

EDIT:
I'm running Feisty 7.04
everything is default not running a custom kernel or anything.
2nd Edit:
Nevermind i think i fixed it;
Forgot to set the uid in the etter.conf
But know i'm getting:
iptables: No chain/target/match by that name

mmmm.... still working on it

---

### Post by lil_malcolmx2 on 2007-07-24
I'm having the same problem can any help PLZ.... :(

---

