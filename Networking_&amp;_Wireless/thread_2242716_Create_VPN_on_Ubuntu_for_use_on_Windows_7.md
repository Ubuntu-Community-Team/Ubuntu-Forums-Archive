---
title: "Create VPN on Ubuntu for use on Windows 7"
date: 2014-09-03
forum: Networking &amp; Wireless
---

### Post by god2 on 2014-09-03
[FONT=arial]Okay, so this could be an extremely stupid question but I've been searching for hours to find this answer. I am going to purchase a Linux server (Providing it's the correct thing to do), and I want to use it to run OpenVPN so I can have my own small VPN. I can't find an answer to the question to if it's even possible. All I can find is threads about how to use an Ubuntu VPN Server on Ubuntu, but not for other OS. If anyone can explain to me how I would go about setting up a VPN on a VPS so I can have a personal VPN for my computer and iPhone it would be much appreciated! [/FONT]:p Also, I don't want to purchase a VPN account as it's "cheaper and less hassle" I enjoy having a little thing to maintain like this, so thanks to anyone who solves my problem, much appreciated :D

---

### Post by weatherman2 on 2014-09-03
Yes, you can.  I have setup several Ubuntu servers that run OpenVPN.  They work well.

Are you planning to use the server for anything besides the VPN?  (File server?)  FYI, it is probably a lot easier to setup OpenVPN on your home router instead of getting a dedicated server just for VPN.  Even if you need a home server, you can still run OpenVPN on your router and wake up the server remotely when you need it.

Most consumer routers can't run OpenVPN, but if you get a router that is compatible with TomatoUSB or DD-WRT firmware, and has enough RAM and NVRAM, you can run OpenVPN on it.  I recommend TomatoUSB which only runs on a small number of routers but is very easy to setup.  Many older Linksys/Cisco and some Asus routers are supported by Tomato.  Even an old WRT54G "G" router (versions 1 - 4) could be used as a home gateway running Tomato firmware and the OpenVPN, but then you'd probably want a newer router/access point for WiFi as "G" is kind of old.  Linksys E2000, E2500, E3000 for example work well with Tomato and OpenVPN.  One of the Tomato developers named Shibby has a list of supported routers on his website:

[http://tomato.groov.pl/?page_id=69](http://tomato.groov.pl/?page_id=69)

---

### Post by rose5 on 2014-09-04
Setting up OpenVPN between Ubuntu and windows is very straightforward. [LEFT][COLOR=#000000][FONT=Arial]You may configure your OpenVPN server, and you have to generate your CA certificate and the server.key file. Please find [/FONT][/COLOR][/LEFT][here]("http://www.howtoforge.com/openvpn-server-on-centos-5.2")[LEFT][COLOR=#000000][FONT=Arial][ ]("http://www.unixmen.com/setup-configure-openvpn-server-ubuntu-13-10/")a full tutorial about installing openvpn on a Ubuntu, the configuration step is the same for any linux OS. Then, take a look to the [/FONT][/COLOR][/LEFT][windows Gui OpenVPN.]("http://openvpn.se/")

Hope it could help

---

