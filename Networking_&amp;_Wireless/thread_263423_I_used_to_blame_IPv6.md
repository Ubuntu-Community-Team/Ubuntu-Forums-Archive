---
title: "I used to blame IPv6"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by Buffalo Soldier on 2006-09-23
I've been using Ubuntu on my Dell laptop since day one I bought it. Everything just works from the very beginning.

During the first year, my surfing habit was 80% at home (static IP) and 20% at college (student lounge). The college wifi was using minimal security, ie. controlling access using MAC address only. Therefore the default Ubuntu/GNOME network control/applet was sufficient for my need.

But early this year, I find myself surfing less at home and more "on the road". And this leads to try and use the Network-Manager applet. My "on the road" experience with Network-Manager is excellent.

But I was having problem with my home router (Aztech DSL600ER). While my static ip experience with it was flawless. Using DHCP on it was giving me nightmares... couldn't connect, disconnection problem, slow speed, problem with DNS and etc.

At first I blamed the IPv6 thingy. So I followed the usual guide on [disabling IPv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4). Editing my dhclient.conf to add "prepend domain-name-servers [insert DNS server here];". This was my setup for the past 4-5 months. Things working OK.

But yesterday, out of curiosity, I applied an upgrade to my router/modem firmware (the latest version: 63.68.1, the previous was 62.xx.x). Enable again my IPv6 and return the dhclient.conf file to default.

To my surpise... my modem/router is working fine with IPv6 now :) Or perhaps it was already working fine with Ipv6, but maybe i did a wrong configuration or something and i was too quick to blame IPv6.

Moral of the story... 
1. once a while check the manufacturer page for firmware upgrade :)
2. don't be too quick to blame something/someone when anything screws up :p

---

