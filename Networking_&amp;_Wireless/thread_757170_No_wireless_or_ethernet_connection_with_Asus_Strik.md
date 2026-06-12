---
title: "No wireless or ethernet connection with Asus Striker Extreme"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by automatedhamster on 2008-04-16
Currently dual-booting Vista and the 8.04 beta on a Asus Striker Extreme 680i. I'm also trying to connect via a BT Home Hub (UK ADSL).

While ubuntu installs more or less okay, there is no networking whatsoever (while in Vista it works fine). It doesn't work regardless of whether I try and set up a static ip or DCHP. The static address should be 192.168.1.66, and the hub is 192.168.1.254. I can't ping the hub itself.

I've tried:

> 
sudo modprobe forcedeth


I've updated the BIOS to 1503 (latest).

The forcedeth driver is *still* "Not in use". 

In fact, I've even tried a wireless card (Cisco), and I can't even get a connection with that.

I've had no such problems under Vista. While in ubuntu, there is definitely a light on the ethernet socket and the BT Home Hub is functioning perfectly - cables and hardware are all fine.

Cheers.

---

### Post by TerabyteUK on 2008-05-22
I am also having problems with this.
Only this is not the beta, this is the final release. Same setup, different isp (bethere).

---

