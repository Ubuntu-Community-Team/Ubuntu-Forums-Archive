---
title: "firestarter can't use device when sharing internet connection"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Nublet on 2008-11-11
recently my router bricked (probably due to some automatic firmware upgrade gone wrong, but let's not go off topic), so i decided to set up my laptop to act in it's place until i get it fixed, or get a new one. after struggling a bit, i managed to set it up to connect to my dsl modem and thus the internet. after struggling more (and not-so-automagically installing dhcp server, duh) i managed to get firestarter to share the internet connection, so all was well.
however, today i've decided to check once more if the router really does not work - and it didn't - after connecting my laptop again, it doesn't share the internet connection anymore!
i checked the firestarter and found out that the firewall is off, and it says that eth0 is not ready (i use eth0 for lan and ppp0 for internet connection). after trying out various configurations i found out that it only says that if i tick "enable internet connection sharing".
so, any ideas about what could have gone wrong?
thanks in advance. :)

---

### Post by Nublet on 2008-11-12
i tried to set it all up on a live session just to make sure i haven't accidentally messed up some configuration files, with the same results. :(
also, i'm not sure if it's relevant, but i'm using an acer aspire 5315 laptop with a broadcom BCM5906m ethernet card.

---

