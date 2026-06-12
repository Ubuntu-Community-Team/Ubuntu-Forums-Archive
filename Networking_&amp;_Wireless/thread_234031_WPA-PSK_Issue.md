---
title: "WPA-PSK Issue"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by viveknz76 on 2006-08-10
Hi,

I managed to get the ubuntu to work with WPA-PSK but everytime I have to connect I have to run this command...

sudo wpa_supplicant -D wext -i ath0 -c /etc/wpa_supplicant.conf -w -dd 

Is there a way of getting away?  Also, I installed the Network-Manager but I am unable to see any icon or open gui.

Thanks

Vivek

---

### Post by Fass on 2006-08-10
To get Network-Manager to manage your connections, you have to comment all of them except "lo" out in your /etc/network/interfaces file.

By the way, are you sure you installed "network-manager-gnome" and not just "network-manager?"

Now, if that doesn't work, and Network Manager doesn't pick up your connections, you can add something like this to the /etc/network/interfaces file:

```
auto ath0
iface ath0 inet dhcp (assuming you have a dynamic IP)
pre-up /sbin/wpa_supplicant -Bw -Dwext -iath0 -dd -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

But, really, Network-Manager is a lot better than the latter hack.

---

### Post by viveknz76 on 2006-08-12
I am sure that I have installed the manager.  I'll try the solution.  Thanks

---

### Post by viveknz76 on 2006-08-13
Hi,

This is my original interfaces file

***********************************************
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

****************************************************

My modified file

*******************************
auto lo
iface lo inet loopback
*******************************

I restarted and still cannot see the Network-Manager-Gnome in my tray.

Please help.

Thanks

---

