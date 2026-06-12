---
title: "Share internet to router for network rendering"
date: 2015-05-28
forum: Networking &amp; Wireless
---

### Post by pieter512 on 2015-05-28
Hello 

I would like to connect all my computers to perform a distributed network render with Blender. 

This is my setup:
[IMG]https://yb7vwg-bn1306.files.1drv.com/y2p6x_KFqheF8fbNjAJa1ARByzyzyggSFILHdcA8_3bkkEh9VsB3Ps21zbPrq-fM6UOO3l7EhEHe3yRKd6PDYoM_BAj6a60JRo1dFxIbmB8S2C5LmAyrKTB8eQDS6S9_3RZicLeMyOb8fu18irZ0txFhw/Network50.png?psid=1[/IMG]

Our VDSL connection is located downstairs, so that's where the modem is. The modem is connected to desktop  A (running Windows) and the TV decoder via ethernet.
I mostly use my laptop upstairs, connected to the modem via WiFi. I've also got some older desktops (that don't have built-in wifi), so when I want to go online on one of these, I use usb-tethering on my phone or the 'shared to other computers' ipv4 option on my laptop. This doesn't allow me to use multiple desktops on the network at the same, however. So to use them for network rendering, I connect my laptop and the three desktops (B, C & D) to an old modem/router, together with some laptops via wifi. I got DHPC enabled on this modem, so every computer gets an IP address and I can just scan for slaves on my master Blender program, and everything works just fine.
There are a few disadvantages however: 
1. I have to disconnect my laptop from the modem downstairs, so I'm offline while rendering
2. I can't just share my wifi over lan like I would without the router, so all desktops upstairs are offline as well, and so are the other laptops.
3. I can't render on the desktop downstairs when rendering on the ones upstairs.

The best solution would be to have my laptop sharing the internet from the modem downstairs over lan, like a wifi-bridge, to the router, and the router connects the desktop to the internet as well.
How should I configure my laptop and the router, in a way that I have one network where every computer can be reached from any other computer, without losing my internet connection?
(One of the desktops has two network cards, maybe this can be a solution if it's not possible with the router?)

Some of the settings on the router are: DHCP and IP, VLAN binding, NAT, Virtual Server, Special Applications, Static Route, RIP, Routing Table, SNMP, UPnP, ...  I have absolutely no idea if any of these settings have anything to do with the kind of network I'm looking for...
My laptop runs Windows 8.1 - Ubuntu 14.04 - Ubuntu 15.04 in triple-boot.

Thanks in advance!
Pieter

---

### Post by pieter512 on 2015-06-17
Anyone?

---

