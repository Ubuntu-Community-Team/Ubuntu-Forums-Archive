---
title: "Weird network config problem"
date: 2017-10-14
forum: Networking &amp; Wireless
---

### Post by blm14 on 2017-10-14
This is such a weird problem with so many pieces, but I figured the ubuntu forums has the highest traffic so I am posting it here...

I have four machines:

1) Windows 7 system running SMB shares, 192.168.1.6 on ethernet
2) Ubuntu 16.04 system running kodi 192.168.1.14 on ethernet also with SMB shares
3) Windows 10 laptop 192.168.1.68 on wifi
4) LibreElec 8.1.2 running on an AMD APU system 192.168.1.8 on wifi

The windows 7 system cannot communicate with LibreElec. I cannot ssh from 192.168.1.6 to 192.168.1.8 but I can ssh from 192.168.1.14 to 192.168.1.8. LibreElec cannot ping the windows 7 system nor can the windows 7 system ping the LibreElec one. The windows 10 laptop can access both SMB shares over wifi no problem and so can the ubuntu 16.04 system. It doesn't appear to be a problem with SMB per se because even ping doesn't work between W7 and LibreElec. I tried turning off the firewall briefly and there was still no way to access it.

Router is an ASUS Rt-N66U running firmware 380.68_4 of asuswrt-merlin.

---

