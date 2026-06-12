---
title: "eth0 missing after removing IPTABLES?"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by buckweat420 on 2007-06-06
Hello, I was messing around with IP tables and broke something. So I figured as a n00b just remove it and reinstall it. so I did a sudo apt-get remove iptables. It got rid of iptables and also another package that it SAID it did not need (Cant Remember off hand it was like ubuntu-?????). Now eth0 is missing, and I have no Clue what happened so any help is appreciated. 

Thanks

---

### Post by nixfaced on 2007-06-07
I'm not sure how uninstalling iptables would cause eth0 to disappear (I believe something else caused that), but for future reference, if you're ever messing around with iptables and you break your connection and you don't know how to fix it, simply run 'sudo iptables -F'.  That will flush the entire ruleset and return you to a default state of allowing all traffic, which will fix whatever iptables is doing to break your connection.

---

### Post by buckweat420 on 2007-06-07
OK i just tried to run sudo ifup eth0 and it gave me this error. /bin/sh: iptables-restore: not found. Failed to bring up eth0. Is there anyway I can just boot to the CD and reinstall the package? If so what do I need to have in my sources.list to read from the CD?

---

### Post by nixfaced on 2007-06-08
I suspect you're running a newer version than I am (I'm on dapper) because my ifup/down makes no reference to iptables.  Run synaptic, the first listing in your settings -> repositories list should be the cdrom.  Check that and reinstall iptables, likely that will fix your problem.  If not, unfortunately I'm out of ideas.  Easy ones, anyway.

---

### Post by kevdog on 2007-06-09
Try just changing the name of your interface in the /etc/iftab file and see what happens!

---

