---
title: "Asus Laptop ans Wireless"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Bob Fletcher on 2008-11-08
I have managed to get my Asus laptop an X50RL working with Ubuntu 8.10 and connected to the Internet using the madfifi driver. The card BTW is an Atheros AR5007EG. 

The peculiarity is that Ubuntu turns the card off just before the login screen. My only way round this so far is by following this code:
[PHP]sudo su
cd /sys/devices/platform/asus-laptop
echo 1 >> wlan
[/PHP]
No I did not work this out by myself I needed a lot of help. My competency is elementary

What I want to do now to to ensure the AR5007EG stays on during boot so that login to the net is automatic. Does anyone know how I can do this.

Bob...
PS: I understand the EEE PC has the same problem with Ubuntu.

---

