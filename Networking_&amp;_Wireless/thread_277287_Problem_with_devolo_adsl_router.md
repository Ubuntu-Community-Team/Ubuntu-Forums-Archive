---
title: "Problem with devolo adsl router"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by kebajonathan on 2006-10-14
[Update] This is a general networking issue on edgy. See the other posts.

Hello,

I've got a problem with the devolo ADSL router of some friend. I have set his computer up form him, using Kubuntu 6.10. At home I could get on thie internet without any problem but with his Devolo router, it doesn't work.
ifconfig shows me that I get an IP, but when I try to ping anything, I get ```
ping: unknown host www.google.ch
```
I tried installing devolo's config utility, which workd quite well, but then, when I try to use it, I get
```

#> sudo dlanconfig eth0
[some greeting]
Please wat.SendPacket: sento error
: Message too long

Unable to send packets

Sorry, exiting!
```

I don't know what to do any more.
Can you halep me? THX in advance

---

### Post by kebajonathan on 2006-10-14
seems to be a bug in 6.10. Strangely it worked at home...

---

### Post by kebajonathan on 2006-10-15
solution:

I'm sorry I didn't write it down but it now works. Also, the PC isn't here so I can't take a look at it directly... This is what I remember:

in /etc/dhcp3/dhcp.conf (or something like that), in the requests section, remove "mtu-"something (the last one).

I also had some issue concerning cups. You just have to configure the printers using the cups config tool on [http://localhost:631](http://localhost:631) (or something)

Have Fun

---

