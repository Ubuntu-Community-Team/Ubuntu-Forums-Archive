---
title: "internet sharing to ubuntu with wifi?"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by andy_satriani on 2005-09-19
halow, i want to ask, i have just installed my wifi driver on acer 3002lci
and now i want to share the internet connection i have on my xp box to my ubuntu through wifi, but i don't know how to set it, can anybody help me :( thx guys ^^

---

### Post by s_p_a_r_k_y on 2005-09-19
so ubuntu has wifi, windows also wifi? You can conceivable setup an adhoc network and share thru windows. 

iwconfig eth1 mode Ad-Hoc
iwconfig eth1 ESSID MYNETWORKNAME

this should then show up on your windows box as MYNETWORKNAME

you will want to setup a DHCP server on either of them or statically link them. Also windows (assuming its the one connected to the internet) shoudl have connection sharing turned on.

This should do it, but I would suggest a wireless router/Access point to do the trick.

---

### Post by andy_satriani on 2005-09-19
thx sparky, i will try it soon, and give the report here ^^

---

