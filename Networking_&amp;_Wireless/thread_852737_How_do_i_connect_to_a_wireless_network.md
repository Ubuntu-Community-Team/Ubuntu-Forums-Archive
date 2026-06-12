---
title: "How do i connect to a wireless network?"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Rickyk on 2008-07-07
Hey everyone, I am wondering how i can connect to a wireless network. I do not have network manager, so i have to do it manually 
I did not understand the stickyed tut, can someone help me please.:)

Thnaks,
Ricky

---

### Post by mikewhatever on 2008-07-07
Use the following commands from the sticky:
> sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

wlan0 or eth1 are often used for wireless, so substitute one of them for <interface>. ESSID would be the name of the network you are connecting to.

---

### Post by Rickyk on 2008-07-07
> **mikewhatever said:**
> Use the following commands from the sticky:


wlan0 or eth1 are often used for wireless, so substitute one of them for <interface>. ESSID would be the name of the network you are connecting to.

I dont know why but this did not work?:confused:

When i do the sudo dhclient command it says there is already a pid file then says killed old client process , removed pid file it also says send_packet: network is unreachable.

---

### Post by Rickyk on 2008-07-08
This did not work?

---

### Post by superprash2003 on 2008-07-09
firstly ensure that you have a working wifi card i mean with drivers installed and stuff.. type iwconfig in the terminal and type output here

---

