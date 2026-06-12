---
title: "Wireless card detected, but will not connect to network!"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Captain M on 2008-03-21
I am doing a clean install of Ubuntu. When I start up the live cd, the first thing I do is check the network connection. I see all of my networks, so I go ahead an try to connect. My network icon just spins, but never connects. After a while, the network manager just exits. I followed [this]("http://ubuntuforums.org/showthread.php?t=485062") guide but still nothing. I remember having trouble back in 6.10 I think. It always just cured itself. Are there any suggestions?

---

### Post by gambrjl on 2008-03-21
have you tried to manually connect it with iwconfig?

Assuming your using DHCP

sudo iwconfig ethX essid youressid mode yourmode key yourkey
sudo dhclient

I'd check the iwconfig manpage for proper usage of the mode and key params and whether you need them or not

network-manager is flakey for me with ad-hoc networks so I just set it manually (but I don't have to use the mode settings on networks without encryption)

---

### Post by JawsThemeSwimming428 on 2008-03-21
Maybe check this out...what type of card is it?

---

### Post by Captain M on 2008-03-21
gambrjl: 'm not on Ubuntu right now, but will try your suggestion when I get home. Yes I'm using dhcp. I'm assuming ethX will be my interface, which is wlan0. What is my mode?

Jaws: It's a Hawking HWG something. It's support by ndiswrapper, but I don't think I need to use that since it has worked out of the box before. Not to mention the fact I already installed it once to no avail.

---

### Post by Captain M on 2008-03-21
I'm just subscribing to this thread. I don't know how else to do it. Sorry

---

### Post by gambrjl on 2008-03-21
> **Captain M said:**
> gambrjl: 'm not on Ubuntu right now, but will try your suggestion when I get home. Yes I'm using dhcp. I'm assuming ethX will be my interface, which is wlan0. What is my mode?


There are several mode options.. (ad-hoc, managed, I'm sure there are more).  

Like I said though, I don't have to specify a mode but I'm only using the manual configuration of "free" wifi places.

I'm assuming your personal wireless network is encrypted so I would just try it with the essid and key for starters

---

### Post by Captain M on 2008-03-21
It's getting an ip from the router, just not connecting. Heres the output from dhclient:

Listening on LPF/wlan0/00:e0:98:be:3d:97
Sending on   LPF/wlan0/00:e0:98:be:3d:97
Listening on LPF/eth0/00:0c:f1:f2:f7:27
Sending on   LPF/eth0/00:0c:f1:f2:f7:27
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 40667 seconds.

---

### Post by Captain M on 2008-03-21
Ok, I just went and tried a manual  configuration (no wep though). set all the settings, unpulgged my ethernet cord, and BAM! It works. All I have to say is why? What is the deal? I know a lot of people are having this problem. Some answers should be posted and pinned. Maybe a Wireless troubleshooting guide?

---

