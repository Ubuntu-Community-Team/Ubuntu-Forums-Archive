---
title: "eth1 not ready"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by alan-1 on 2007-12-09
Fire starter reports that my fire wall status is disabled.
Failing to start because device eth1 is not ready.
I had been trying to get a usb wireless device to work but failed (it worked perfectly well with Puppy linux)
I connect to my router no problem on eth0 (wired)
All I want to do is erase all trace of eth1 and the wireless device and get back to a single wired connection that the fire wall accepts.
I am an Absolute Beginner and will need very simple instructions can any one help please.

---

### Post by ruibernardo on 2007-12-10
Hi alan-1, :)

apparently you have eth1 defined in the file /etc/udev/rules.d/70-persistent-net.rules, although you don't have that network interface connected. Edit this file with, for example:
```
gksudo gedit /etc/udev/rules.d/70-persistent-net.rules
```You should have two lines line like this:
```
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:00:00:00:00", ATTRS{type}=="1", NAME="**eth0**"
```Comment the line that have **eth1** in the end with a cardinal in the beginning of the line, or delete it. Then reboot with that network interface disconnected from the computer. The next time the computer boots, it will only look for and find the wired interface. No more traces of eth1, just eth0.

Hope it works.

---

