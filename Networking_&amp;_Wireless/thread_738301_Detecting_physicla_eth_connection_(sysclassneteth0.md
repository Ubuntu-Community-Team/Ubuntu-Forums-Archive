---
title: "Detecting physicla eth connection (/sys/class/net/eth0/operstate)"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by chocolatetoothpaste on 2008-03-28
Hi, all.  I'm trying to detect if the ethernet cable is physically plugged in.  In 7.10, I would check the contents on /sys/class/net/eth0/operstate, which would say up or down if the cable was plugged in/unplugged, but in 8.04 (I'm using beta right now), it only says down if the interface is actually down, even if the cable is still plugged in.  I tried checking dmesg and tail /var/log/messages.  They don't log this action.  Does anyone have another idea for checking if the cable is plugged in/unplugged?

---

### Post by chocolatetoothpaste on 2008-03-28
I just had a thought: would the hotplug system know if my ethernet cable was plugged in?  If so, is there a log for the hotplug system I can check for changes?

---

