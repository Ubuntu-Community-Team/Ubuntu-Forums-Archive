---
title: "DHCP, two network cards and Fixed IP's, How do I make them work?"
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by Dragnovich on 2005-10-09
Hello I had just finished installing a network of 16 Stations (all them runing Slackware Linux) This installation is for an office that wil be using a program (web based), that will be running in an INTRANET Linux Server (Near all the s will had not access to the INTERNET), also all stations had Slax installed on the HD (An Slackware linux). And Slax use DHCP to provide IP to each PC. 

So I think Ok lets Mount 1 server with two Network cards, 1 card will receive the LIVE INTERNET CONECTION (provided by my ISP), so I can get Internet in that PC, and in the second network card I will conect an Network cable directly to the HUB. This second card will have a FIXED IP (intranet) like: 192.168.2.1, so I can make it a DHCP server. The plan was good but...........

Problem No. 1:
I Conected the 2 network cards to my PC, and installed Ubuntu, the installation program DETECTS the two cards (it even ask me to choice the one that will be the main card), but when I finally got to the ubuntu system (Network Configuration menu) I got just eth0 at some IP (that my ISP gives me), But I cant see the second card! how do I configure Ubuntu to DETECT both cards. (looking in the connected devices, I can see both cards too), But it seems that I just need to "MOUNT" it some where :D

Problem No. 2
In the only card I got detected (eth0) I try to FIX the ip to mount the DHCP server, but I cant access the configuration. I click in the "Configure" buton it ask me the "root password" i put it and NOTHING HAPPENS!! so how do I configure and FIX the IP manually???

Problem No. 3
How can I install the DHCP server :D  (do you know the commands)

Problem No. 4
I need to SHARE the internet connection JUST for 2 more PC's so, can I restrict them BY DHCP or is bether to use a PROXY insestead of DHCP and fix all network IP's ???

I hope you can help me I try searching but did not find any responce for those questions! :confused: 

Thanks

---

