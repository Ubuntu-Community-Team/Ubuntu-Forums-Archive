---
title: "Configuring Network on boot takes too long"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by evilXhwnd on 2006-08-08
Hey everyone, I've be able to get my wifi card to work,  Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller, using NDIS wrapper and able to connect to my wireless network at home that uses WPA encryption. However, this only works once i've logged in and am inside gnome. During the boot process when it reaches the configuring network part my machine will take a long amount of time before it moves onto the next step. I assume this is because in my interfaces config my wireless card is set to acquire an IP address from DHCP. Here is my interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```

And since it cannot acquire one it just waits till it times out. I have tried switching dhcp to static and that gets rid of the wait in configuring network, however, once in gnome, i cannot connect to my wireless network, it does not show up inside the NetworkManager gnome applet. Anyone have any idea on how i can possible fix this?

---

### Post by evilXhwnd on 2006-08-08
oops, forgot to mention that eth1 is my wireless card. :)

---

