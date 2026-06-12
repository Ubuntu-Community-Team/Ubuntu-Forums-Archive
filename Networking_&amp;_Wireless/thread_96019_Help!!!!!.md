---
title: "Help!!!!!"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by ScottLH on 2005-11-27
I am new to linux and just installed ubuntu. I have a wireless pci card by DLINK it is the DWL-G520M. I cannot seem to figure out how to get this to work. I have never used linux before, but I am very impressed. Please can someone help me!!!

---

### Post by mindwarp on 2005-11-28
System->Administration->Networking

Should look like: [http://static.flickr.com/8/11230002_ee41ca2d3a.jpg?v=0](http://static.flickr.com/8/11230002_ee41ca2d3a.jpg?v=0)

---

### Post by ScottLH on 2005-11-28
OK, I went and it said it was not active so I made it active, it still did not work. the light on the card still didn't come on. it was eth0 not Ath0

---

### Post by mindwarp on 2005-11-28
Does your router do DHCP, SSID broadcast and did you enter those details in?

---

### Post by ScottLH on 2005-11-28
Not sure but I think so, I don't know if my wireless card is even istalled on unbutu, how can I check to see if it is. Where do I enter the info for the card the DCHP and the SSID.

---

### Post by towsonu2003 on 2005-11-28
[QUOTE=ScottLH]OK, I went and it said it was not active so I made it active, it still did not work. the light on the card still didn't come on. it was eth0 not Ath0[/QUOTE]

eth0 is usually the ethernet card. don't look for the name of the interface (eth0 vs. ath0 or wlan0) yet. it should however say "wireless connection" in there. to me, it seems like your wireless card is not configured yet (light not turning on). if that is the case, try searching the forum for ndiswrapper howtos... briefly, ndiswrapper will enable you to install windows drivers in linux for wireless...

---

