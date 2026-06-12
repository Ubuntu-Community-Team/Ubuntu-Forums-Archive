---
title: "vpnc can connect fine, but drops my wifi connection."
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by rentacop on 2008-08-07
Hey guys, I have a rather strange situation.

os     : ubuntu 8.04 x64
conn   : wifi ( connected no issues )

when i do a ifconfig i can see my current wifi device w/ the ip. 

I installed vpnc so i could connect to a cisco vpn. When i try to connect to the vpn it connects fine. 

Now here is the problem. Once it says i am connected to the vpn my network manager says that i am connected to my wifi ssid and the vpn client both at the same time ( good ) but i can't access any site via wifi, nor can i use my vpn connection.

i do ifconfig again and i see both my wifi and vpn interfaces running. 
When i disconnect from vpnc i am able to access the net again.

I can ping my local default gateway but nothing outside of that.

 If anyone knows what might be wrong help would be grateful!

---

### Post by rentacop on 2008-08-08
Me again, after a few hours of tinkering i realized that it wasn't updating ANY dns settings for /etc/resolv.conf because i had a static dns server set up for a unused network card set. 

I disabled the static dns and it worked like a charm. However, DNS for my wifi card isn't updating. Anyone know how to update both rather than just my VPN?


Thanks!

---

