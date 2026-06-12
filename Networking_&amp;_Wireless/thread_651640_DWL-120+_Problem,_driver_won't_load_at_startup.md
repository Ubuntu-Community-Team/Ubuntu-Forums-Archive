---
title: "DWL-120+ Problem, driver won't load at startup"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by GoldenKevin on 2007-12-27
A second ago after I finally got my D-Link 120+ working, I was so happy.  Now, after I restarted my computer, I ran into a problem. I don't know what's going on, but it seems as though my drivers wouldn't load on startup or something.  The device appears to be on and fine, and the light on it shows it should be communicating with my computer properly.  However, Ubuntu thinks it's a ethernet device. By the way, it runs on a ACX100 driver (which took me forever to install).  I found a fix though typing "modprobe -r acx" and then typing "cd /usr/src/acx-20071003" (the directory in which the driver is installed in), and then typing "sudo -s" to log in as root, then "insmod ./acx.ko" (what is a .ko file anyway?).  After a while typing that, it seems the computer then recognizes it as a wireless device.  My question is, is it possible to load this device without having to type all that stuff at startup?  Thanks in advance, and I'm a total noobie to linux btw.




EDIT: It seems as though this problem is totally random.  I just started up my computer again and it seems as though the device is working fine.  I'll try to find what the real problem is.

---

### Post by GoldenKevin on 2007-12-30
Nevermind, I figured out what the problem was.  Apparently there was a conflicting driver in /lib/modules/<Linux Kernel/wireless/acx/acx.ko or something like that.  I simply backed it up, removed it, then copied the new module from /usr/src/acx-20071003/acx.ko to that directory.

---

