---
title: "Satellie Pro 6100 laptop looking dead and gone --need serious help"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by jerrynewt on 2011-03-17
My daughter's Toshiba Satellite Pro 6100 has maverick installed and she lost her wi fi. So I was going to try and go back to 10.04 where her wi fi worked just fine. I got home yesterday and fired up the laptop with the 10.04 disc, and couldn't get the comp to boot from the cd drive (DVD/CD RW). Tried to set the bios to boot from the cd drive and no go. It still goes straight to the hard drive trying to boot. Thing is after the initial boot screen pops up for bout two seconds I get this message on an otherwise black screen

No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

  After the last entry there is a blinking cursor. Dunno what's going on but it don't look good. If I could just get the cd to boot I could install the 10.04 but no luck so far. Any help would be appreciated sooooo much.
  The laptop has 250 gig hd with 768 M ram. Before this started the system worked flawlessly with exception of no wi fi.

---

### Post by Hedgehog1 on 2011-03-18
> **jerrynewt said:**
> My daughter's Toshiba Satellite Pro 6100 has maverick installed and she lost her wi fi. So I was going to try and go back to 10.04 where her wi fi worked just fine. I got home yesterday and fired up the laptop with the 10.04 disc, and couldn't get the comp to boot from the cd drive (DVD/CD RW). Tried to set the bios to boot from the cd drive and no go. It still goes straight to the hard drive trying to boot. Thing is after the initial boot screen pops up for bout two seconds I get this message on an otherwise black screen  **No init found. Try passing init= bootarg.**

The symptoms are not promising.

This could be 'Catastrophic Chain Failure' (where each component failure causes the next one to fail); Or, it might be a series of little things.

If WiFi **was** working OK on maverick, and then stopped, and now the HDD seems to be acting up and the CD wont read, it sounds like controller failures on the mother board.

If WiFi **never** worked on meverick, and now the HDD seems to be acting up and CD seems to be not reading, it could be the HDD is failing on it's own and the CD is old/scratched enough to not appear to be readable to the laptop.

If you make a clean install CD of 10.10 (if wi fi worked on it) or 10.04.2, burning it at the slowest speed.  If you can boot off this, save any data from the drive and check the drive health (Disk Utility).

It sounds not-so-good, but a 'rescue attempt' is worth making.

Also - do you smell burning electronics when it is powered up?  Does your daughter recall the laptop shutting down on its own, perhaps with an 'overtemp' warning?  Use your hand to check for really hot spots underneath.

***The Hedge***

:KS

---

