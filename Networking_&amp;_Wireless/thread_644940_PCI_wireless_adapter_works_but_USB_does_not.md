---
title: "PCI wireless adapter works but USB does not"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by nfergusson on 2007-12-19
I recently puchased a Linksys WRT54G router which works (internet access) out of the box with Ubuntu 7.10 when hardwired between my DSL modem and PC. My company laptop (Windoze 2K) sees the router and can connect using its internal wireless adapter. My other desktop, on the other hand,:
1. Works fine when a PCI wireless network adapter is installed. I can see the other machines (ping, ssh, etc), and can get to the internet.
2. Does not work with a USB adapter. The computer sees the wireless network, and shows it as having a decent signal strength, but will not connect. I cannot ping the router (192.168.1.1).

I have tried:
1. Completely removing the netcard (old-fashioned wired netcard), and plugging the USB net adapter into different USB jacks, including the ones on the front.
2. Browsing to the config setup on the router and ensuring the firewall is turned off.

Is there something I am missing?

---

### Post by stalker145 on 2007-12-19
> **nfergusson said:**
> I recently puchased a Linksys WRT54G router which works (internet access) out of the box with Ubuntu 7.10 when hardwired between my DSL modem and PC. My company laptop (Windoze 2K) sees the router and can connect using its internal wireless adapter. My other desktop, on the other hand,:
1. Works fine when a PCI wireless network adapter is installed. I can see the other machines (ping, ssh, etc), and can get to the internet.
2. Does not work with a USB adapter. The computer sees the wireless network, and shows it as having a decent signal strength, but will not connect. I cannot ping the router (192.168.1.1).

I have tried:
1. Completely removing the netcard (old-fashioned wired netcard), and plugging the USB net adapter into different USB jacks, including the ones on the front.
2. Browsing to the config setup on the router and ensuring the firewall is turned off.

Is there something I am missing?

Check the [Hardware Page]("https://wiki.ubuntu.com/HardwareSupport") for your particular USB adapter. I recently set up my youngest son with a Linksys WUSB54GC. I *thought* it was plug and play, but when i tried connecting to any of the half-dozen networks it saw (encrypted and not) it failed. I found out I had to actually change drivers, use ndiswrapper, and dance three circles around the fire under a full moon ;)

---

