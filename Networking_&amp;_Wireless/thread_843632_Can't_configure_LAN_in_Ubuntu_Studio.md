---
title: "Can't configure LAN in Ubuntu Studio"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by Aritomo on 2008-06-28
Well, I recently installed Ubuntu Studio 8.04 and had a pretty hard time setting up LAN. 
First of all, the machine - it's an old laptop with Realtek RTL8139 ethernet. My neighbour runs normal Ubuntu 8.04, connecting through Realtek RTL8169, and it work just fine for him. We're both connected to the same ASUS Giga X1005/G router, and that one is connected to the campus' LAN.
So, we both can't use DHCP for automatic configuring - this has something to do with the lame ISP here. DHCP works only in Windows, and has been told to hang and reboot certain routers. Guess, there's nothing we can do here.
So, we configure it all manually - using the Win settings. The standart LAN configuration utility doesn't work either somehow, so we do it through ifconfig. That is where my neighbour's Ubuntu starts to work fine. To me, however, the fun only starts.
Basicly it looks this way: after entering all the necessary settings in /etc/network/interfaces, upon ifconfig, eth0 shows up as configured properly. But the packet statistics is at 0 and I can't ping anything in LAN.
MTU, configured to be 1492 may change to 1500 randomly
I tried to setup manual routing following [this]("http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html#more-531") tutorial, however whenever I try to add a route with a gateway (being 10.1.3.254 and randomly changing in ifconfig to 10.1.3.255  occasionaly somehow) it responds as "no such process" unless there's already a route there with this gateway (which happens when using the otherwise useless in my case configuration utility). If I try to add routing config to /etc/network/interfaces, upon restarting the networking service, it fails to reconfigure.
The funniest thing however is that SOMETIMES, after hours of randomly tinkering with all these settings, it suddenly starts to work. Then I happily setup pppoe, go online, update the system, I might reboot it several times, even boot to XP, but when I don't use Ubuntu for some days and then boot back - it's dead again.

[SIZE="1"]I wouldn't even bother with Studio, but my midi-keyboard lags under XP, so I really wanted to test it with the realtime kernel, but alas I cannot go online to fetch some tutorials on setting it all up or a driver for the keyboard[/SIZE]

So please, somebody, help?

---

### Post by Aritomo on 2008-06-30
Anyone?

---

### Post by Aritomo on 2008-07-01
Please?

---

