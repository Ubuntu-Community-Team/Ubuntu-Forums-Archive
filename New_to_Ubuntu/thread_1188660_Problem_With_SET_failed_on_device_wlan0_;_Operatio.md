---
title: "Problem With SET failed on device wlan0 ; Operation not permitted."
date: 2009-06-15
forum: New to Ubuntu
---

### Post by judavi on 2009-06-15
Hi!

I'm newbie, and don't talk to much english, but I will try expose my problem.

I'm triying to pass my wireless card to master mode doing this

iwconfig wlan0 mode master

and receive this mesagge

SET failed on device wlan0 ; Operation not permitted.

after I tried to do this

sudo rmmod ath_pci; sudo modprobe ath_pci autocreate=ap

and received this message

module ath_pci does not exist in /proc/ atheros pci

Please I need to convert my Wireles card to master mode to make an acces point.

Thanks,

---

