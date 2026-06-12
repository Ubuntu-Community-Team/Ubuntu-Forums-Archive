---
title: "Wifi card wont connect to wireless repeater"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by mister_p_1998 on 2008-11-23
Got a strange one here guys.
Ive just built a Hardy install to use for Xbox Media Center to sream videos from my server wirelessly. Ive got a Belkin PCI 80211 wifi card and a Belkin Wireless repeater. My PCI card can SEE my repeater, but wont connect to it, . Ive got MAC address security enabled and this is setup right,if I disable MACC address security it does connect but with zero connectivity, all I get is an IP. I can connect to my neighbors Wifi on it no problems.

Everything works perfectly on the wired network.

---

### Post by shanix on 2008-11-23
Any message from the /var/log/syslog ??

---

### Post by Joe2Shoe on 2008-11-23
In Edit Connections/Ipv4 Settings, choose Automatic (DHCP).

---

### Post by mister_p_1998 on 2008-11-24
> **Joe2Shoe said:**
> In Edit Connections/Ipv4 Settings, choose Automatic (DHCP).

In Network? on the Router? where?
Ive already got DCHP enabled, I think..
It connects fine on the neighbors router

---

### Post by Tom--d on 2008-11-24
Its probably due to the encryption you are using on your Wireless.

Maybe your wireless card (or driver) cannot handle the new encryption, WPA. (Thats if your on it).

---

### Post by mister_p_1998 on 2008-12-01
Fixed it, changed from frequency 13 on the wifi router to Frequency 1..
sorted
Steve

---

### Post by Kangarooo on 2012-10-10
> **mister_p_1998 said:**
> Fixed it, changed from frequency 13 on the wifi router to Frequency 1..
sorted
Steve

Theres no logic in that. I have TL-WR340G router set as my country where 13 channel is legal. When i tried to make my repeater TL-WA500G to find it it couldnt find it. Then in wireless settings i changed country to mine and saved. Then in repeater settings it found it. You had router settings problems. If its working ull see in repeater how good is connection and that it has found correct channel. Also do a firmware upgrade.
I now have bigger problem. My repeater works in Windows but not in Ubuntu. Its now for 1/2 year ive changed different settings and setups and repeater not working and one friend with Windows was able to connect so now im reporting a bug.

---

