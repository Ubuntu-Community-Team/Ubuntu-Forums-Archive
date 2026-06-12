---
title: "How to troubleshoot a wireless connection?"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by Ragueneau on 2006-07-30
I'm trying to create a WPA connection on my Xubuntu Dapper laptop through wpa_supplicant, but I'm running into issues.  

The process, as I've seen it outlined, is that ifconfig associates with the router, runs dhclient, and then starts wpa_supplicant to establish communication.  Unfortunately, dhclient always times out in this process, even sitting directly on top of the router.  

I can log in automatically if I comment out the wpa business in /etc/network/interfaces and if I turn off security, but only under those circumstances.  Also, since I only intend to work with a single access point, I'd like the network connection process to be automatic at boot. 

Where should I start looking for problems?

---

