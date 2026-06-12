---
title: "WPA works, Wireless Works but not connecting to my AP"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by ubuntufans on 2005-11-15
Hi Guys,

I've been having bad problemw ith wireless lately

My WPA works fine with the madwifi drivers, i have netgear 311 V1

But it';s connecting to my neighbour instead of my AP

however if i type ifdown ath0 and ifup ath0 manually after login then it will connect to my AP

any idea why it's doing that?

---

### Post by mlomker on 2005-11-15
Are you specifying your access point's ESSID in your /etc/network/interfaces file?  By default it'll connect to the strongest signal.  If you run gnome then you could trying using **network-manager**.

---

