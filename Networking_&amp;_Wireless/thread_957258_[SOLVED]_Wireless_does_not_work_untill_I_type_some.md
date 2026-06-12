---
title: "[SOLVED] Wireless does not work untill I type some commands in..."
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by Dark Samurai on 2008-10-24
Hey-
When I start up Ubuntu, the wireless does not automatically pick up the signals.  When I paste ```
sudo modprobe b44
sudo modprobe eth0
sudo modprobe ssb
sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe ndiswrapper
dmesg | tail
sudo /etc/init.d/networking restart 

```
in (with some fiddling of the order some times) it works.  Is there any way of making the wireless work on its own from the start-up?
Thanks!

---

### Post by melojo on 2008-10-24
add them to 
/etc/rc.local before the exit line

make sure it is executable.

---

### Post by Dark Samurai on 2008-10-26
Thanks!  (I actually went to this website [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and installed the stuff it told me to)

---

