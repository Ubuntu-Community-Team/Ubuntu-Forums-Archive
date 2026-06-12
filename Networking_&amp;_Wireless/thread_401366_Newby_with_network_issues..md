---
title: "Newby with network issues."
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by codahowe on 2007-04-04
Hi all.  Brand new to the Linux world.  Got a a copy of 5.10 the other day and decided to check it out.  Put it on an old clobber box at the office and the install went flawlessly.  I however cannot get on the web to update and get add-ons.  I can browse my office network easily and poke around out Win XP machines, but still now outside access.  Everything looks fine in the hardware setup but again, I can't be sure since I'm new.  I'm not sure about the DNS and going staitc vs. auto.  I have a simple network on an old Aopen router.  Any ideas?

Thanks,

---

### Post by rolando on 2007-04-08
have you set the default gateway to the outside? (ie. the local IP address of your router?)

Open a termianl and type

sudo route add default gw 192.168.1.1 (or whatever your local IP address is of ADSL router).

Youll only have to do it once.

:)

---

