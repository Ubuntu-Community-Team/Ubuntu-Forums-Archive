---
title: "How do I get dhclient to work automatically?"
date: 2005-08-27
forum: Networking &amp; Wireless
---

### Post by numberexhaust on 2005-08-27
All right... I have a netgear wg511T card that works fine with ndiswrapper (I've tried madwifi, not working well with that) and I have just one complaint.  When I start the computer I have to manually run "sudo dhclient wlan0" before I can connect.  I'm using the ESSID "any" and dhcp, because I take this laptop on many networks, as it is a school laptop.  I would like for this command to be automatic as I won't have much time to worry about kinks when school starts, especially when I'm using it in classes.

Thanks

---

### Post by ishift on 2006-10-09
i have the same situation, except my wireless card is the broadcom 4306.

any help?

---

### Post by ishift on 2006-10-10
bump :D

---

### Post by Iowan on 2006-10-10
Post your /etc/network/interfaces file.

---

### Post by ishift on 2006-10-10
```
auto lo
auto eth0
iface lo inet loopback

```

---

### Post by Iowan on 2006-10-10
I don't have wireless, but I suspect there should be a :
```
auto wlan0
iface wlan0 inet dhcp
```
or something similar...
The **auto wlan0** should make it configure on startup.

[http://www.ubuntuforums.org/showthread.php?t=12045&highlight=%2Fetc%2Fnetwork%2Finterfaces]("http://www.ubuntuforums.org/showthread.php?t=12045&highlight=%2Fetc%2Fnetwork%2Finterfaces") 
Perhaps something in here might be more useful.

---

### Post by dennis1200 on 2006-10-14
i have the same problem, on a broadcom 4318 (the one and only! what a disaster). writing in dhclient to the rc.local file doesn't work either, though my network interfaces already has the eth1 connection as dhcp. i don't really mind typing in sudo dhclient every time i start but it is annoying, also because firestarter gives an error message about the device not being ready, then i have to start it again. here is my interfaces file:

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid XXXXX
wireless-key XXXXXXX

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

