---
title: "Wifi won't start automatically at system boot?"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by rainerigs on 2008-01-20
Could somebody help out a real nube?  I got my wifi working after a lot of fiddling around with ndiswrapper but my wifi interface will not start automatically when I boot my computer.  When I configure the interface manually after the system has booted it works fine. I know I need to edit my network interface file but I am not quite sure what to do for my particular configuration.   My wifi is connected only on eth2 when I configure it manually, eth0 is my wired connection that I rarely use.  Any help would be appreciated.

Here is the output from the  "gedit /etc/network/interfaces":

auto lo
iface lo inet loopback




iface eth1 inet dhcp
wireless-essid PeachNet
wireless-key 6CED2B08A2E9347CDE660A973F

wireless-essid PeachNet
wireless-key 6CED2B08A2E9347CDE660A973F

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





wireless-essid PeachNet
wireless-key 6CED2B08A2E9347CDE660A973F





wireless-essid PeachNet
wireless-key 6CED2B08A2E9347CDE660A973F


iface eth0 inet dhcp







iface eth2 inet dhcp
wireless-essid PeachNet
wireless-key 6CED2B08A2E9347CDE660A973F

























auto eth2

---

### Post by Hightide on 2008-01-20
you may find Kevdog's thread useful


[http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857)

:)

---

### Post by kevdog on 2008-01-20
Id suggest first cleaning up your interfaces file -- you have things listed twice, under eth0, etc.  Second what is eth1?  You have eth0 and eth2, but what is assigned to eth1?

---

