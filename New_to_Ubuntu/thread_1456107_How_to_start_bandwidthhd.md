---
title: "How to start bandwidthhd"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by donescamillo on 2010-04-16
Hi,

I installed (through Synaptic) bandwidthd in order to keep an eye on my network traffic. After the installation I looked in all menus (accessories, System tools etc) but it was not there. So I run Synaptic again, found bandwidthd, right-clicked and fount that it was in /usr/sbin.
So I went to usr/sbin and double-clicked on it and nothing happened. I created a launcher on the desktop pointing to /usr/sbin/bandwidthd but it did not work.
How do I start this file?

thanks,
donescamillo

---

### Post by Monotoko on 2010-04-16
I havent used bandwidthhd before, but this should work:

Open the terminal (System -> Accessories -> Terminal) and type: "bandwidthhd"
You may need to type "sudo bandwidthhd" though if it requires root.

---

### Post by donescamillo on 2010-04-16
I tried,

now it says "Cant open ./etc/badwidthd.cfg"
I thought the program would have GUI.

donescamillo

---

### Post by grifonas on 2010-04-16
> **donescamillo said:**
> 
How do I start this file?


Have you seen this HOWTO:
[http://infodotnet.blogspot.com/2008/02/install-and-configure-bandwidthd-per-ip.html](http://infodotnet.blogspot.com/2008/02/install-and-configure-bandwidthd-per-ip.html) ?

According to them you're supposed to have [libcap]("http://www.tcpdump.org/"), [libpng]("http://www.libpng.org/"), [libgd]("http://www.boutell.com/gd/") and [apache]("http://httpd.apache.org/") installed on your system as well. 

Apologies if you've seen it already.

---

