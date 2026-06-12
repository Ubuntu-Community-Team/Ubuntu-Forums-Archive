---
title: "Can Ping router, but can't ping other computers on network."
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Awia1 on 2008-04-27
I can ping my router but not other PCs on the network, I also can't get on the internet using Firefox or traceroot to an outside IP.

I used to be able to get away with this by opening firefox as soon as Ubuntu started, but after updating to Hardy, the startup is too long, so I can't get to it fast enough.

---

### Post by yeleek on 2008-04-27
> **Awia1 said:**
> I can ping my router but not other PCs on the network, I also can't get on the internet using Firefox or traceroot to an outside IP.

I used to be able to get away with this by opening firefox as soon as Ubuntu started, but after updating to Hardy, the startup is too long, so I can't get to it fast enough.

Is this a manual ip config or dhcp?  are you on the right subnet and do you have your router specified as your default gateway?

check via ifconfig and route -n

---

### Post by Awia1 on 2008-05-03
Sorry I've taken so long to answer.

It's DHCP, but I've managed to get it to work. I have to manually input the DNS settings, but it just forgets them every now and again, any idea why?

---

