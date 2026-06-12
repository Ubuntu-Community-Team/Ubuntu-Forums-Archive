---
title: "UPnP port-forwarding command line tool?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by iX9 on 2010-05-06
Hi!):P
Is there any UPnP port-forwarding command-line tool?
I found some, but I can't compile them, I am just beginner...
ThanXz;)

---

### Post by -humanaut- on 2010-05-06
Have you tried looking through synaptic?

---

### Post by Hospadar on 2010-05-06
For any sort of network configuration on the command line, the ultimate tool is iptables, which is installed be default (i believe), but it's not particularly user friendly (it's designed to give full power to network administrators and the like).

If you do some google searches about iptables you'll come up with something.  I googled "iptables upnp port forward" and got this as the first result: [http://www.dd-wrt.com/wiki/index.php/Port_Forwarding](http://www.dd-wrt.com/wiki/index.php/Port_Forwarding) at the bottom there are some iptables commands (the stuff on top is for dd-wrt, a linux-based firmware for certain routers)

---

### Post by jinnk on 2010-06-21
There is an implementation of uPnP for linux.  It's called the linux Internet Gateway Daemon, linux-igd, and can be found at [http://linux-igd.sourceforge.net/](http://linux-igd.sourceforge.net/)

---

