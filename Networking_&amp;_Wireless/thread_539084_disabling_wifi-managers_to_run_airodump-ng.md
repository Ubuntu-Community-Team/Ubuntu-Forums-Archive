---
title: "disabling wifi-managers to run airodump-ng"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by aminahmadi on 2007-08-30
Hi 
I need to stop the wireless card from roaming and connecting to networks while I try to run airodump-ng.

How could I do that? 
I use airomon-ng and put the card in monitor mode
start airodump 
and starts collecting, but then it stops and I notice the wireless has connected to some network, which is annoying as hell. 

I tried removing, uninstalling, wifi-radar but it still does that? 

how could I stop this machine from trying to help me by automatically connecting? it shouldn't be that hard!

This is on Fiesty Fawn installation with an Intel card on eth0 

thanks
amin

---

### Post by wirelessmonkey on 2007-08-30
edit /etc/network/interfaces and comment out the line for your wireless card. It will be something like "auto dhcp wlan0"

---

### Post by aminahmadi on 2007-09-01
I commented the related lines with ## but it still connects to some available network?


any other ideas?


Thanks

---

### Post by aminahmadi on 2007-09-01
Uninstall wifiradar, and I could go 
ifconfig eth1 down 

but after 300 bacons it connects again. It seems like the commenting doesn't do anything, the DHCP is disabled but the annoying auto connect thing is there

---

