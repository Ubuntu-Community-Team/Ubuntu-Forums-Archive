---
title: "ubuntu server"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-12-24
I'm trying to set up a ubuntu server, and i cant get on the Internet, I know it a DNS issue,
I can ping my router but not get DNS to work
ifconf = ip 192.168.0.70 sn 255.255.255.0 gw 192.168.0.1
how do i see my DNS setting in ubuntu?

---

### Post by deputy on 2008-12-24
If you're behind a router, then the router will most likely have the DNS information.

---

### Post by halitech on 2008-12-24
this might sound obvious but can you ping beyond the router? try google by IP 74.125.45.100

---

### Post by ibizatunes on 2008-12-24
I can ping external, no problem, just cant ping any DNS same outside of my network

---

### Post by gpsmikey on 2008-12-24
Two things come to mind -- 1) you don't happen to have the router set to block internet access for machines not in the "OK" list (if you have set that up).  2) this would not happen to be an SMC router with older firmware and you are running only static IP addresses would it?  I ran into an issue a couple of years ago with an SMC7004 Barricade router where it would not forward the DNS requests (like it is supposed to) unless DHCP was enabled on the router LAN side (even if not used).  Newer firmware fixed the issue, but it took a bit to find it !!

mikey

---

### Post by The Cog on 2008-12-24
If you are using a static IP address, you also need to set the DSN server addresses yourself. These are in /etc/resolv.conf with lines that look like this:
> nameserver 192.168.0.1
In the above example, the nameserver is a local router, but you may need to enter your ISPs DNS servers in there instead.

---

### Post by ibizatunes on 2008-12-24
Thanks that fixed it, i didnt have nameserver 192.168.0.1 
was pointing 192.168.1.0 - must have set them up wrong when i was setting the server up :lolflag:

---

