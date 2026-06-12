---
title: "how to scan lan network open port via public ip"
date: 2016-12-11
forum: Networking &amp; Wireless
---

### Post by hasan5599 on 2016-12-11
Hi expert guys......I have router and 5 or more computer running in my Lan network which ip address are 192.168.12.12 , 192.168.12.102 etc. And I have gotten a public  ip addressess like 182.211.189.142 which is same all of my laptop public ip addresses.....I know how to scan open port by nmap  in LAN network ( 192.168.1.1/25 ) but don't know how to scan Lan network via public IP address . I want to test sequrity issue so bought another router to check my Lan network so I want to scan all of my LAN network via public ip . How to do it ??? Please inform me .....

---

### Post by TheFu on 2016-12-11
sudo nmap 182.211.189.142

The routes need to allow this. Some home routers block requests to the public IP of the router as a security thing to prevent really smart javascript from opening unintended ports.

There's also internet-based port scanners.  grc.com has one, just don't buy into his "stealth" BS.

---

