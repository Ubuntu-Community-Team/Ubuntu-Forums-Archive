---
title: "Network manager"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by somersetsimon on 2006-10-22
I'm struggling to get my wireless connection working. I was advised to use network-manager, so I installed it from the alternate cd. First time I ran it, all the 'connections' part was greyed out and it claimed there were no networks. I was then told I had to alter my /etc/network/interfaces file to edit out all my networks (except lo)

I did this and rebooted. Network manager still showed nothing. Earlier, when I had enabled wlan0 in Network settings, the light on my device was green. When I changed the above file, the light stays off when I boot up. How is network manager supposed to find anything when the devices are all disabled?

I'm going to give network manager one last go, then try wi-fi radar, so any advice on nm would be appreciated.
Thanks

---

### Post by joergenlie on 2006-10-22
Which network driver are you using? I can't get nm to work with a compiled ndiswrapper 1.25, it works with the bcm43xx-fwcutter, but the connection is slow.

Jørgen

---

### Post by somersetsimon on 2006-10-22
Do you mean device driver? It's a ZD1211B for my USB stick. When I enabled it with the 'standard' commands, iwconfig and iwlist seem to find the device and the wireless network ok, but I just can't connect.

---

### Post by joergenlie on 2006-10-23
post your iwconfig here

Jørgen

---

### Post by somersetsimon on 2006-10-24
The outputs from various networking commands are in another post on networking problems.

[http://www.ubuntuforums.org/showthread.php?t=280176](http://www.ubuntuforums.org/showthread.php?t=280176)

Is there anything I should try?

---

### Post by joergenlie on 2006-10-24
Before you try network manager, try to get connection without it.
uninstall it
Enable your interface in network settings.

try the command: "sudo iwconfig wlan0 ap any" if you still get no access point.

if you see light on your card, thats better than no light with natwork manager.

Jørgen

---

