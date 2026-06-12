---
title: "4311 works, but will not function after trying to bring the card out of monitor mode."
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by irishguy515 on 2008-11-16
hey everyone,

so i have 8.10 and my b43 driver(i have a 4311 rev 2 card) is working great for most uses, including monitor mode and packet injection.

my problem is that when i switch to monitor mode with kismet or something of the like, i cannot bring the card back to managed mode. more precisely, i can set it to managed mode after downing the interface wlan0, but when i bring it up, it will not correctly associate with any AP.

currently all i can do is restart, but thats a real pain, is there a way i can re-initialize the driver, or somehow simulate a restart but only for the driver? i hate having to restart.

also, just in case it matters, i have a second interface called wmaster0, i don't really know what its for, but i have tried playing with it in combination with wlan0 to no avail.

TL;DR

how can i reset my (open-source) b43 driver without restarting my whole system?

---

### Post by irishguy515 on 2008-11-17
so i've tried resetting NetworkManager, but that hasn't seemed to do anything else either.

any other ideas?

---

### Post by Ayuthia on 2008-11-17
It sounds like you have already done this:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed essid someplace
sudo ifconfig wlan0 up
sudo dhclient wlan0
```
The other thing that you could try to do is reload the b43 modules:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
```

---

### Post by irishguy515 on 2008-11-17
> **Ayuthia said:**
> It sounds like you have already done this:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed essid someplace
sudo ifconfig wlan0 up
sudo dhclient wlan0
```
The other thing that you could try to do is reload the b43 modules:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
```
Awesome, worked exactly as it did before. thanks a ton.

---

### Post by archman on 2009-02-08
WOW awesome, my card 4311 can go monitor mode now!!!!!! (intrepid)

---

