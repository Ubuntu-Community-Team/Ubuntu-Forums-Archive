---
title: "Can't Find Wireless Network But No Problem At Work"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by 3UR1Q on 2008-04-01
Hello All,
I've tried multiple avenues  to make sense of this but I have had no luck so far. I am new to Linux but I have a decent understanding of networking. I've reached a deadend so I'm hoping someone can help.
I can find my router and all surrounding networks using my Vista partition. The router is broadcasting and I have disabled security completely. If I reboot under the Ubuntu partition I do not see any wireless access points. I originally though that I needed a iwfi driver but wasnt sure, so I took it to my buddy at work. I was able to find multiple access point around work effortlessly. Obviously my card is fine so I came back home. Still no luck.
I can plug in directly to the router and pull an IP. No problem.

**sudo Iwlist wlan0 scanning returns:**
*[I]Failed to read scan data : Resource temporarily unavailble*[/I]

**Iwconfig returns:**
lo "no wifi...."

etho "no wifi..."

wmaster0 "no wifi...."

wlan0  IEEE 802.11g ESSID:""
Mode:Managed Frequency:2.412GHZ Access-Point:Not-Associated
Retry min limit:7 RTS thr:off Fragment thr:2346 B
Link Quality:0 Signal Level:0 Noise level:0
Rx invalid nwid:0 Tx invalid crypt:0 Rx invalid frag:0
Tx excessive retriies:0 Invalid misc:0 Missed becon:0


Fresh install of Ubuntu 7.10 on 10GB partition running Vista. Intel 4965 AGN Mini. Linksys WRT54GS currently at default setting with no security. I know there are other brand routers in my area that Ubuntu is no seeing as well.Any direction with this would be greatly appreciated. Thanks!!!

---

### Post by kevdog on 2008-04-01
Can you list

lshw -C network
ifconfig

---

