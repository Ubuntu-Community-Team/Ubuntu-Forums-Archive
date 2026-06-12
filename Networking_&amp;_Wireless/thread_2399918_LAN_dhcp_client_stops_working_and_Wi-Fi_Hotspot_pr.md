---
title: "LAN dhcp client stops working and Wi-Fi Hotspot problem"
date: 2018-08-31
forum: Networking &amp; Wireless
---

### Post by pnck on 2018-08-31
Hello, 

i can't connect to Internet through DHCP. My desktop use Ubuntu 18.04 desktop with latest update. DHCP client gets no IP address. Static configuration works perfect. When i use dhcp i see "Activation of network connection failed" 

[https://snag.gy/YZdP0m.jpg](https://snag.gy/YZdP0m.jpg)

One end of cable connect to my pc and another end to ISP. ISP have DHCP server and reservation for my mac address. I was trying to connect this cable to another pc's (ubuntu 18.04 and windows) with changed MAC.

I was trying to remove profiles from NetworkManager and reinstall network-manager package [https://askubuntu.com/questions/637637/how-to-reset-network-manager-to-default/637683](https://askubuntu.com/questions/637637/how-to-reset-network-manager-to-default/637683)

I pasted some configuration information to [https://paste.ofcode.org/4Mv4sRA72nJk554TaHyTbJ](https://paste.ofcode.org/4Mv4sRA72nJk554TaHyTbJ)

This problem happened after i connect this pc directly to another ubuntu pc for filesync through cable with static ip configuration.

After that with this problem i got not working wifi. I can't connect to wifi networks and nobody can connect to wifi hotspot from this pc.

---

### Post by pnck on 2018-09-01
I did fresh installation Ubuntu 18.04. Everything was OK after installation. However it brake down after :sudo apt dist-upgrade" So static configuration works perfect however automatic(DHCP) configuration is failed.

This is some additional information in attachment

---

### Post by pnck on 2018-09-01
I connected PC to LAN wifi router and it got IP from router DHCP server. So
1. ISP with another ubuntu 18.04 pc and windows work perfect. 
2. My pc with ubuntu doesn't get ip from ISP
3. My pc with static configuration works ok
4. My pc with windows2go get ip from isp
5. My pc with ubuntu got ip from dhcp on router

---

### Post by pnck on 2018-09-03
This is syslog [https://paste.ubuntu.com/p/G7mJrbKpsH/](https://paste.ubuntu.com/p/G7mJrbKpsH/)
This is dhcpdump [https://paste.ubuntu.com/p/3Y9mcVcxN5/](https://paste.ubuntu.com/p/3Y9mcVcxN5/)

---

### Post by pnck on 2018-09-03
This is dhcpdump from ubuntu 18.04 livecd [https://paste.ubuntu.com/p/DJQYvD7zDb/](https://paste.ubuntu.com/p/DJQYvD7zDb/)

---

### Post by pnck on 2018-09-04
Hello,

I did wireshark research and found that dhcprequest goes with incorrect checksum. This is difference between livecd and installed ubuntu 18.04. LiveCD DHCP client sends correct checksum and installed sends no checksum. Wiresharks says: "Frame check sequence: 0x00000000 incorrect, should be 0x0140e56a"

There is wirechark file in the attachment. The first 3 packages from livecd and another packages from installed after reboot.

Is this bug? Where should i post it?

Best regards

---

### Post by wildmanne39 on 2019-01-04
Thread closed, it is only attracting spam!

---

