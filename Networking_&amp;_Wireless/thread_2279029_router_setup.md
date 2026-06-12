---
title: "router setup"
date: 2015-05-20
forum: Networking &amp; Wireless
---

### Post by atux on 2015-05-20
hello everyone.
i do need some for my home office.
there is an adsl which is so slow and unstable
3g connection with 10GB/month
wifi from community.

i do need to have constant connection to internet.
i have a micro pc with 3 ethernet ports(eth0, eth1, eth2)  and usb. ubuntu 12.04(server) is already installed 
i do need to setup this pc to act as my gateway. here is what i need.
-wifi (wlan0) from usb stick. ssid:public_A, wpa2, passwd:whatever, IP address:192.168.0.34/24 gateway 192.167.0.1
-3g modem from vodafone
-adsl IP address:192.168.2.56/24 gateway 192.168.2.1

I need is to have all of these connected and active. give a taffic shape of 200kbps to 3g, 500kbps to wifi and 600kbps to adsl.
i do need to give priority to adsl, then wifi and finally to 3g. also if there is an application that can manage multiple sessions then use all 3 connections.
the local lan port (eth1) will have the IP address:192.168.5.1/24.
all traffic to these 3 wans to get nated from eth1.
please some help, since i am working on some projects that i need constant internet for my home office.

---

### Post by atux on 2015-05-21
In connection to my previous post i have found the [http://ubuntuforums.org/showthread.php?t=2214561](http://ubuntuforums.org/showthread.php?t=2214561)
it seems nice. the questions that i have are:
-how do i implement 3g in that.
-how do i rate limit each connection differently.

---

