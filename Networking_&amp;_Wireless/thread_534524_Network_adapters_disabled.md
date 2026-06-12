---
title: "Network adapters disabled"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by turtle02 on 2007-08-25
I just installed ubuntu server 6.06. when i do a ifconfig the only adapter if get is my internal loopback.

when i run the lshw command i see that my wireless adapter and my nic card are disabled what is the command to enable these interfaces.

---

### Post by Darkhack on 2007-08-25
What are the devices?  They may not be compatible out of the box.  Post the part of the output of lshw that shows the device.

---

### Post by turtle02 on 2007-08-25
thanks anyway i found the command sudo ifconfig eth0 up

---

