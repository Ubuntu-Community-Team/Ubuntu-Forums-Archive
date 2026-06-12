---
title: "Vpn through Vodafone e172 stick"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by quigon on 2008-04-24
Hello everybody:

i'm new with ubuntu, but i used linux a some time ago. Well, now i want to start using linux for my bussiness, but i have a little problem. Every thing works well except vpn connection to MS 2003 server through the e172 vodafone modem.

If i use wired or wifi networks vpn works well, but with this modem nothing appears to do.

I've been reading some post in this forum and i think that the problem is that vpn connection (pptp) try to connect with eth0 or eth# interfaces, creating a ppp0 interface when it connects. The problem is...
1. The connection must be established using ppp0 instead eth
2. the vpn connection must not use ppp0, because that interface is already in use.

i try to add a route like this:
```
sudo route add -net "public ip of my server" netmask 255.255.255.255 dev ppp0
```

but not work.

Anyone can help me?

please, sorry for my english


thanks

---

### Post by quigon on 2008-04-26
nobody has a solution?

i'll try in hardy next week.

Thanks

---

