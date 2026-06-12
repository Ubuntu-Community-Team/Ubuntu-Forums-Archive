---
title: "Wired to wireless"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by Stealth on 2005-04-16
Hey guys, I had installed Kubuntu Hoary on my laptop, surprised to see everything working awesome (except suspend, almost perfect! ^_^) and noticed how I was able to use my wireless (integrated IntelProset thing) on different occasions (logged in at my uncle's hous to his network). My problem is at home, I used an ethernet cable to my netowrk, since atm I do not have a wireless router. However I plan on buying one next week. My question is how do I get Kubuntu to start using the Wifi as the default network connection? I remember during setup that it asked me about the 2 network interfaces, but I useed the ethernet at that time. Now if I go somewhere else and boot Kubuntu, it will freeze for about 2 minutes, apparently trying to find the ethernet thing or something (wish that was faster, teh cable's not plugged in, just skip it!) Now how will I change it to the wireless?

---

### Post by nautilus on 2005-04-16
If you open up this file in a text editor, it'll show your interface(s):

/etc/network/interfaces

Mine looks like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

```

mind pasting yours, so then... we can tell you what to change :D

i have the exact same setup, but went the other direction, i took wlan0 off and am now using eth0 exclusively (a full-size PC with a wifi card in it, weird, i know)

---

### Post by Stealth on 2005-04-17
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
 script grep
 map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
```

---

### Post by Stealth on 2005-04-19
Would I just need to change eth0 to eth1 under the primary nework interface section?

---

