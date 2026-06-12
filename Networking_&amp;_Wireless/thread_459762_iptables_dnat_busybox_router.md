---
title: "iptables dnat busybox router"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by RaZer0r on 2007-05-31
hi

I switched ISP recently (from cable to DSL) and with that i bought a modem with an ethernet connector (rj45) and dsl (rj11). At first the modem crashed all the time, reconnected etc... I'm hosting some websites and use my ip in the A-name records of my dns server..., as these ip's had to be static, I searched a way to get my modem more stable. I did a successfull firmware flash from an Acorp firmware (my modem is a D-Link T320) Now running stable for weeks...
The only problem i have is that everyone gets redirected to the correct folder of my virtual servers on apache config... All but the comps running behind the server (which is also my gateway to the internet). I figured out it had to do with my eth0 which gets an 192.168.1.2 ip instead of the public ip it used to have with the cable ISP. 

So now my question is, does anyone know how to set up my router (the new firmware switched the modem to a router with dhcp etc...) so to forward the public ip correctly to the server? 

I tried some iptables commands (which i can't recall bc I got them of a copy paste help friend :p)

someting as iptables -t nat -A POSTROUTING --destination externalip --to-destination 192.168.1.2 (server ip)

If anyone could help me out, it would be greatly appreciated :)

---

### Post by RaZer0r on 2007-06-01
bump no one?

---

