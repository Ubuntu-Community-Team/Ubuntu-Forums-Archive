---
title: "Avoid getting eth1"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by pk_rulz on 2008-02-26
Hi 

I am using a Dell Inspiron 1520 with Reliance Wi Max.

It gave a really hard time starting with ubuntu but finally i learned that it was due to Avahi

I removed both avahi-daemon and avahi auto-pid from my system using package manager

so i no more get eth0:avah

But still I get a eth1.  Can any 1 tell me what is that and how can i get rid of that bcoz unless I bring that down my machine is unable to get a IPv4 addr required for me 2 connect 2 internet

Thanks
Pradeep

---

### Post by SpaceTeddy on 2008-02-26
eth0:avahi is the autoconfiguration if your network card does not receivce any dhcp offers

eth1 would be your second network card (either wireless or lan) and you can get rid of it by unloading the drivers for the card.

Why that is neccessary is beyond me, tho...

---

