---
title: "Network bridge for eth0 and wlan0 has no IP address"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by nfox on 2007-12-14
Hi, 
I have a Wii WiFi USB dongle and am trying to turn it into an Access Point for my house. I have used NDISWrapper to install the driver (Buffalo NETU2G54) and it works beautifully.

Once I have it up and running, the WiFi light is flashing and I go over to one of my laptops (Vist-sucks) and I not only find the network but I can fully connect to it-- no problem. I do ifconfig on my server and it shows no IP address and no access point selected. 

I tried to bridge eth0 and wlan0 with bridge-utils and whenever I bind eth0 I lose internet. The only info I found was to make br0 and bind eth0 on 0.0.0.0 and wlan0 on 0.0.0.0 and then ifup br0 and it should work. It no worky. An IP of zeros seems absolutely wrong but the forums show this works....


**Problem #1:**
How do I save my wlan0 configuration since a reboot erases the network device? I've configured /etc/network/interfaces but I think it is overwritten on startup.

**Problem #2:**
I have no IP address for wlan0. Bridging **eth0** and **wlan0** via **br0** apparently requires those interfaces to be bound to 0.0.0.0 according to other posters. This is simply not working. I just need an IP for wlan0. 

**** Details:**
I'm on Feisty, DSL connection at 192.168.1.254 and my box connects around 192.168.1.93/97. I have a Xubuntu laptop with wifi card and a Vista laptop with built-in wifi.


Any help is appreciated. I've found a relatively simple solution for Windows and I would hate to require it just to bridge my wifi.

Also, if anyone wants to get the drivers (it's a Windows oriented package but pretty simply to translate to linux) to get their Wii/DS wifi dongle to act as a (very strong I might add) router let me know and I'll upload the software.

---

