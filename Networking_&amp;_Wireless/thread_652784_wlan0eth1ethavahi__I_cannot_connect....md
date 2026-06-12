---
title: "wlan0/eth1/eth:avahi ??? I cannot connect..."
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by mrking88 on 2007-12-29
Hi all,

I have this wireless connection problem. Whenever I want to switch network, it will seems like it got stuck somewhere.

I would use "Preferences > Network" to turn off wLAN and turn it back on again. With some  try and luck, I would get the "eth1:avahi" and sometimes "wlan0" interface... I am using the "network manager" applet that resides on the menu bar.

Again, SOMETIMES wlan0 would work and if it is the eth1:avahi, I would need to edit it to be "eth1" in the "network manager" and SOMETIMES it worked. Yea as you see, with all these uncertainties, I am getting really confused, I can't spot the exact problem.

Some things for sure, driver is fine(using ndiswrapper), nothing wrong with wireless interface, I would expect it to be some software problem.

FYI - Wireless is working greatly on ubuntu feisty with wicd, changing network and logging onto encrypted network using wicd works just fine. It's after the upgrade to ubuntu gutsy that I have all these problems.

I have removed wicd as it's not working anymore maybe due to the problem above.
Below is my /etc/network/interfaces

> auto lo
iface lo inet loopback

#iface eth0 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

iface eth0 inet dhcp

auto eth0

iface wlan0 inet dhcp
wireless-key 88342428842548678384100495
wireless-essid Elf's router

auto wlan0

auto eth1
iface eth1 inet dhcp
wireless-essid mrking's router

Pls help.

---

