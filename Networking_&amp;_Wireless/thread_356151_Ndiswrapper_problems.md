---
title: "Ndiswrapper problems"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Fundi on 2007-02-08
I'm trying to get the netgear wpn111 wireless adapted working. So far i have run the following commands:

tom@TomsLaptop:~/src/netgear$ sudo ndiswrapper -i netwpn11.inf
Installing netwpn11
tom@TomsLaptop:~/src/netgear$ sudo ndiswrapper -l
Installed ndis drivers:
netwpn11        driver present
tom@TomsLaptop:~/src/netgear$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
tom@TomsLaptop:~/src/netgear$ sudo gedit /etc/modules
tom@TomsLaptop:~/src/netgear$ sudo gedit /etc/modules
tom@TomsLaptop:~/src/netgear$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

When I run the command sudo modprobe ndiswrapper i get an error that I don't understand. Can anyone tell me how to fix it?

---

### Post by Corvo78 on 2007-02-08
I know for sure that executing "ndiswrapper -l" shoud return:
[i]Installed ndis drivers:
xxxxx driver present, **hardware present**[/i]

So, naturally you can't get your wireless to work.
Have you tried ndiswrapper-utils-1.18 package instead of the 'regular' ndiswrapper-utils??
I remember that solved my 'Invalid argument' problem.


_edit:_
Follow this link [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902) and have a look at 'problem 2'.

---

### Post by bvmou on 2007-02-08
Sometimes, as happened to me, the driver provided by the manufacturer doesn't work, in my case it was that the default driver in the windows executable was 64 bit.  The ndiswrapper website lists a bunch of drivers known to work, which are not always what you'd expect.

Could you post the output of the command: dmesg | grep ndis (or dmesg | grep ndiswrapper, I cant remember exactly which.)?

---

