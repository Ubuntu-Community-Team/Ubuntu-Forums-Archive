---
title: "OpenDNS on the router"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by Draylorre on 2007-09-25
So, I decided to go all hXc hardcore-dizzlerizzle and added the openDNS addresses to my router's DNS

if I edit my resolve.conf to just my routers address 192.168.0.1 could I just get the DNS and alt DNS from my router instead of putting in the two from open DNS?

Do I even have to configure DNS on my linux-box now?

---

### Post by scrooge_74 on 2007-09-25
If you dont give any permanent DNS server addresses to your PC, it would take them from your provider or in this case from your router.  By giving your router the IP if Open DNS servers you are bypassing your ISP (wich in my case will drop their DNS servers from time to time and leave to dry), I did gave my router OPEN DNS addresses, but all of my laptops have the IPs prepend anyway since I do move around a lot and have to connect to other people routers

---

