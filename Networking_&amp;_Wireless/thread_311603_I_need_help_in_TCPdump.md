---
title: "I need help in TCPdump"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by kfupmer on 2006-12-03
dear guys,
I got this problem  when I use the live cd:

tcpdump: socket: Operation not permitted
also alot of other problem that I can not write to my HDD.

Regards,
Shaheen
[http://student.kfupm.edu.sa/s215759](http://student.kfupm.edu.sa/s215759)

---

### Post by spd106 on 2006-12-03
First check that the interfaces are up and working. It should appear in the notification panel. Try specifying an interface to use and run it as root i.e. if you have eth0 try **sudo tcpdump -i eth0**. To find out which interface name you have, run **ifconfig**.

To access the hard drive partitions you may have to mount them. Check out the mount man pages for options.

---

