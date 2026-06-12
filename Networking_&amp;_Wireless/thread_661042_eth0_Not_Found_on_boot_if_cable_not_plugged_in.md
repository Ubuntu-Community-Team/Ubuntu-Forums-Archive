---
title: "eth0 Not Found on boot if cable not plugged in"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by robmacg on 2008-01-07
Hi,

I have a Thinkpad T60 running Gutsy. If it is plugged into the LAN when the system is booted eth0 is activated correctly and works fine (for example, if I unplug the cable, it automatically tries to connect the wireless network, then if I plug it in again and disable wireless it switches back). 

However, if the LAN cable is plugged in after boot time, I cannot activate it. I see:

[FONT="Courier New"]rob@skylark:~$ ifconfig eth0 
eth0: error fetching interface information: Device not found[/FONT]

Looking in /etc/network/interfaces I see no mention of eth0. I tried adding this to it:
[FONT="Courier New"]
auto eth0
iface eth0 inet dhcp[/FONT]

This changed the result, but not much:

[FONT="Courier New"]rob@skylark:~$ ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device[/FONT]

running sudo /etc/init.d/networking restart gives the same result. 
So it seems clear that the interface has not been discovered at all. I've checked that the module is loaded with[FONT="Courier New"] modprobe e1000[/FONT] and lsmod show it.

Any ideas?

---

### Post by theether on 2008-05-20
Hi,

I have the same problem, also on a T60 with Hardy.

Did you ever find a solution to this?

Cheers.

---

### Post by theether on 2008-06-17
Hi,

I created the following file that resolves the issue when I resume from suspend:

/etc/acpi/resume.d/61-eth0.sh 

#!/bin/sh
# Remove and insert the NIC kernel module to fix eth0 not shown
/sbin/modprobe -r e1000
/sbin/modprobe e1000
/etc/init.d/dhcdbd restart
/etc/init.d/networking restart

Cheers,

Jamie.

---

