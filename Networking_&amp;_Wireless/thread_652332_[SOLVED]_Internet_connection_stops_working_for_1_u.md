---
title: "[SOLVED] Internet connection stops working for 1 user account"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by brett611 on 2007-12-28
I've been on Ubuntu for a month and have had zero internet access problems.  I have 2 user accounts (brett + sue).  Both have been working fine.  I connect via a hard wire to a router.  Again, this has never been a problem.  "brett" is my main account - all references below refer to actions taken in this account unless stated otherwise.

Yesterday I installed Guarddog but couldn't figure out how to config it...it blocked all internet connectivity.  I uninstalled it via Synaptic and everything was fine.  Today everything was working fine until 30 minutes ago.  I tried to install MS Money via Wine.  It said it was successful yet I couldn't find it installed.  So I rebooted.  After the reboot I lost all internet connectivity - firefox, widgets, updates, etc.

Yet logged into "sue" account everything works fine.  I am entering this post via the sue account now.

As a point of reference I am useless when it comes to command line functions, thanks to 15 years of MSFT's OS.  So please don't say "flush iptables" without also providing painfully explicit instructions.  As another point of reference I don't know how to view iptables, ipfreely (ha) or fstab.  Anything via terminal commands exceed my current understanding.

Help is most appreciated!

---

### Post by brett611 on 2008-01-01
It appears I'm a victim of pilot error.  Starting Firestarter fixed this problem.  However, given that I have been encountering beaucoup issues with improper mounts, fstab, iptables, compiz...I did a full reinstall and all problems solved.  So solution is - don't $&#^# around with stuff unless you know what you're doing and how to undo it!

Still took less time than XP SP2 install!!

---

