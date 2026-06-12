---
title: "Ports for Transmission remain closed, port forwarding performed"
date: 2017-08-08
forum: Networking &amp; Wireless
---

### Post by david-black267-q on 2017-08-08
I tried to download files using Transmission but the application report that the connection failed every time. Then I found the port that the application was listening was closed. After some research done, I did port forwarding on my router and add rules to my firewall to allow the port but the result is still the same. I even tried "iptables -A INPUT -p tcp --dport 51413 -j ACCEPT" which didn't work. 

I'm running out of solution.

---

### Post by igdfpm on 2017-08-08
Have you opened both TCP and UDP as bittorrent (generally) makes use of both - also double check that the forward in your router is pointing to your correct local address this may change if you have not also set up a static ip for your local machine ;)

---

### Post by david-black267-q on 2017-08-08
I opened both and I have specified my IP address. I saw someone on the internet recommend to disable firewall. I tried without any progress

---

