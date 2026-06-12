---
title: "Connect 2 WiFi NICs to 2 APs at the Same TIme"
date: 2016-08-21
forum: Networking &amp; Wireless
---

### Post by uRock on 2016-08-21
Hi all!

I am excited to have finally attempted getting the SwannView Android app to work in Chrome by following the instructions on [https://www.linux.com/learn/installing-android-apps-linux-archon](https://www.linux.com/learn/installing-android-apps-linux-archon)

My PC has two wireless cards and I have two access points(APs). 

AP1 is my primary network with Internet connectivity. 
Default Gateway 10.0.0.1 (255.255.255.0)

AP2 is my Security Cam network with no network connectivity. Swann has zero security functionality, so I want it segregated.
Default Gateway 10.0.2.1 (255.255.255.0)

I want to be connected to both networks at the same time. I know I have to add some entries to the routing table, but I am lost on how to do it.

Could someone please tell me how or point me in the right direction?

Cheers & Beers,
uRock

---

### Post by uRock on 2016-09-04
I seem to have fixed this issue by going into Network Manager and editing the connection to the router with no Internet. Checking the box in Routes to "Use this connection only for resources on its network".

---

