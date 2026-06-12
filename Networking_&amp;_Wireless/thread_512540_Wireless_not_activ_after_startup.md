---
title: "Wireless not activ after startup"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by KlaasP on 2007-07-29
I recently upgrade to Feisty. Managed yo get my Atheros wireless card working using valuable info from this forum, but only after issuing "sudo /etc/init.d/networking restart".
This is how the relevant part of my /etc/network/interfaces looks like:
auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-ssid Peernet
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk * hex key*
What should  I do to have my wireless activated during startup

---

### Post by kevdog on 2007-07-29
Please re-read the WPA post by Weiman.  This is a documented problem with the way you are setting it up.  A solution was proposed by sticking a script in the rc.d file (I believe).  Again the post is a sticky located at the top of the networking forum, I believe the solution is on page 3 or 4.

---

