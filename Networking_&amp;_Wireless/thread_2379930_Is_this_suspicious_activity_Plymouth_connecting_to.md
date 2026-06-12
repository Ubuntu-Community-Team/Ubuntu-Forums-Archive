---
title: "Is this suspicious activity? Plymouth connecting to unknown network"
date: 2017-12-11
forum: Networking &amp; Wireless
---

### Post by jimijives on 2017-12-11
Hi, 
I'm quite new to Ubuntu. I started using it after my computer got hacked.
I eventually had to dispose of my laptop as the virus seemed hardware based.
I got a new laptop and I'm a little paranoid about getting hacked again so I've disabled WiFi on my ISP's cable modem and also the WiFi adaptor on the laptop.
This is what is concerning me.
After installation of Ubuntu 16.04 the computer started performing an action without any input from me. How is it connecting to a network when I have WiFi disabled?
Thanks for any advice.


Started to tell Plymouth to write out runtime data.

Reached target network (Pre)
Set Console Scheme
Created system-getty slice
Started LSB: App Armour
Starting raise network interfaces
Reached target network is online.
journalctl -xb
system logs
systemctl reboot
systemctl default
Control-D to continue

---

### Post by QIII on 2017-12-11
Hello!

Do you have an ethernet connection?

---

### Post by jimijives on 2017-12-11
Hi QIII,
thanks for replying. I do have ethernet and my aim is to use that and remove WiFi connections altogether.
I haven't connected the laptop to the internet while I installed Ubuntu, that is why I find a network connection strange.

---

