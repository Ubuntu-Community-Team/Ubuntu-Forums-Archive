---
title: "network-manager problem"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by chaosdesigner on 2008-08-08
I know that this is a really stupid question but I just not seem ot find a solution. I have ubuntu 8.04, so i guess network-manager has to already be installed. But where is it? How do I start it? Under System > Administartion are only 2 Apllications with Network: Network and Network Tools. Is the network-manager one of them? If not, how do i start it?

chaosdesigner

---

### Post by dca on 2008-08-08
Network Manager by default starts in your system tray in the top right of your screen by the clock.
 
If it's ethernet it looks like a monitor, sometimes two depending on the theme/icon theme used.
 
If you have a properly recognized wireless card and you left-click once it should have a drop-down indicating wireless networks in your area.

---

### Post by Avinash.Rao on 2008-08-08
That will also give you an option to configure your network interfaces.

---

### Post by chaosdesigner on 2008-08-08
Oh right, thx.

I must have installed my wirelles usb Driver wrong because i can only see the two Monitors. I have a Fritz Usb Device so if anybody can give me some advice, that would be great.

---

### Post by okey666 on 2008-08-08
Your card may be working...do
```
sudo iwconfig
```
and see if it comes up with any cards with wireless extensions.

---

### Post by chaosdesigner on 2008-08-08
like I said, i have an usb wlan Device, so when I type "lsusb" its shown as:

Bus 002 Device 014: ID 057c:62ff AVM GmbH WLAN USB v1.1 [no firmware]

So i gues the problem is firmware, which is weird cause it should be installed. I installed it with NdisWrapper.

Edit:

I solved the problem, thx for your help.

---

