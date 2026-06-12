---
title: "Disable dnsmasq in Ubuntu 16.04"
date: 2018-03-20
forum: Networking &amp; Wireless
---

### Post by mathieu-tarral on 2018-03-20
Hi,

I'm trying to setup a company VPN, but my **/etc/resolv.conf** is rewritten by dnsmasq, which tries to resolve domains locally on **127.0.0.1:53**

Now I searched a bit, and found that i could disable it in** /etc/NetworkManager/NetworkManager.conf.**

I commented the line [B]dns=dnsmasq
[/B][ATTACH=CONFIG]279006[/ATTACH]
I restarted NetworkManager, but **dnsmasq refuses to go away.**
I even rebooted my laptop, and still dnsmasq is here.

Is there a **bug** in NetworkManager ?

Thanks for your help.

---

### Post by slickymaster on 2018-03-20
Thread moved to **Networking & Wireless** for a better fit

---

