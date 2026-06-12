---
title: "Wireless problem, find it but no connect!?"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by MightyMike on 2007-01-08
Hi,

I have a wireless network problem, my **connect2air wlan 5400** doesnt work. When ifconfig i find it as eth2 with correct mac address.  **I dont have any encryption**, i want it to work first. I tried ->system -> administration ->network and activated wireless. I did the same thing on my other pc, a laptop... it worked right away (atheros wireless).

When that didnt worked i installed netmanager and wifi radar. Still no success, same problem. I tried ndiswrapper and used my xp drivers "prism2"... no luck at all. Same problem. No property driver (or something).

**Why is it eth2? Shouldnt it be ath0 or something else?**

I get no  ipaddress, ill tried to use a static ip and set SSID, no luck either.

I use Ubuntu 6.10 on a fujitsu siemens scaleo t pc with connect2air 5400 d1700 wireless card.

I have googled a lot with no luck... please help :)


I installed linux mint 2.1 (built on ubuntu but with lots of network applications) , **it recognize my card and im able to choose it from network manager**. _But i get no_  ip, and i dont use any encryption at all.** I should have maximum signal strength becouse the router is very close. But no signal at all.**

Thx and best regards!

/Mike

---

### Post by Crooksey on 2007-01-08
Ok run

```
 
iwconfig eth2 essid "your essid"
dhclient eth2

```

---

