---
title: "Is dnsmasq preventing internet access?"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by marinecomm on 2014-06-18
On my computer I have dual boot Win 7 and Xubuntu 14.04 64-bit. Tonight I switched over to Xubuntu to work on something. When I fired up Firefox it acted like I didn't have an internet connection. Dropbox wouldn't connect either, however Spotify would play. I am hardwired to my router. I checked UFW and found a whole slew of ports that said were being used by dnsmaq. I was doing some port forwarding yesterday and these ports with dnsmasq were not there. I fired up my laptop which is connected via wi-fi thinking maybe I could use it to look for a solution online. It showed the same behavior. Web browsers acted like there wasn't an internet connection, Software Updater wouldn't download packages. It said to check my internet connection. I turned on my wi-fi hotspot on my phone and connected both computers to it. Connected to my phone I have internet access again. I can't figure out what dnsmasq is doing or if it is conflicting with something. The only thing I can think of is that I configured network manager and my router to use OpenDNS servers. Could there be a conflict with that? When I'm running under Win 7 I have full internet access.

---

### Post by marinecomm on 2014-06-18
I happened to run dmesg and got the following:

[ 1815.254608] [UFW BLOCK] IN=eth0 OUT= MAC=(my mac address):04:a1:51:d5:b0:fa:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=278 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=54018 LEN=258

---

### Post by marinecomm on 2014-06-18
Ok, looks like I got it solved. According to this article [http://xmodulo.com/2012/12/how-to-use-custom-dns-server-on-ubuntu-desktop.html]("http://xmodulo.com/2012/12/how-to-use-custom-dns-server-on-ubuntu-desktop.html"), dnsmasq conflicts with custom DNS settings so you have to disable dnsmasq first then add in the custom DNS servers to network manager. Once I disabled dnsmasq it restored my internet access.

---

