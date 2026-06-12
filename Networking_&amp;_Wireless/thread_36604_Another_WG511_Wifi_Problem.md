---
title: "Another WG511 Wifi Problem"
date: 2005-05-24
forum: Networking &amp; Wireless
---

### Post by makisupa123 on 2005-05-24
First time Poster...please be kind.

I followed several different threads here and got my Netgear WG511 working with ndiswrapper.  The key was to delete and killfile prism54.  Now, the card works every OTHER time the machine boots.  On the boots where the nic fails the usb driver doesn't work and neither does the sound.  I get an error message saying HAL fails after a very long boot time.Then some of the gnome applets fail (desktop switcher, trash, etc).  Rebooting hangs the system, then a hard boot, then it works (after I activate it in the gnome network applet).  Its quite odd.

Anyone got any ideas what's going on?

Machine is a Dell Inspiron 2500 with 512 MB of RAM.  Please make responses appropiate for a recovering windows user.

THanks

Mak.

---

### Post by makisupa123 on 2005-05-24
Alright...I figured out what's going on here....sort of

If the PCMCIA card remains plugged in on restart, hotplug will take forever and the strangness occurs.  Same is true on a cold boot if the card never lost power from the subsequent session.  IF. on the other hand, you either unseat the card on reboot or remove all power from the laptop (whatever, the important thing being that the card is reset) the next boot will work.  In other words, ndiswrapper can start the card, but not shut it down.  Any ideas how to completely shut the PCMCIA system down (as in no power) on restart?


Thanks,
mak

---

