---
title: "WICD with WPA encrypted network help!"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by moyam01 on 2008-11-29
I was able (thanks to the forum) to get my rtl8187b card working with ndiswrapper and a driver that I found on the forum. As long as the network is not encrypted I can connect to it, but as soon as I enable encryption it becomes a problem. Whenever it feels like it will connect to the network, but then suddenly it drops out. (in a matter of seconds). I read somewhere that I have to modify some sort of template, but I have no idea what that means. So basically I am stuck with no idea what to do next.

My setup:
Linksys WRT54G
Toshiba a215-7422 (RTL8187b)
Hardy Heron running ndiswrapper and wicd

Any help will be appreciated

---

### Post by CSandman on 2008-12-01
My University uses Encrypted WPA so I've dealt with similar problems.
First you need to make sure you know the info about the network:

Security:  WPA/WPA2
EAP:  PEAP/TLS/TTLS (PEAP is most common)
Key Type: AES-CCMP/TKIP/Dynamic WEP (TKIP is most common)
And of course your login "identity" and password.

Then you right click on the Network Manager and choose "Edit Wireless Networks".  In that dialog you select the ESSID you need to configure and put the info in.  When you're done close that and try to connect again; this time it should work.

If you don't know what Security Protocol, EAP, and Key Type is used you have to resort to random guessing.  If you're the admin for the network consider using a simpler protocol until you have this sorted out.

---

