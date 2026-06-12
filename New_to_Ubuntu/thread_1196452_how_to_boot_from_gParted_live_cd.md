---
title: "how to boot from gParted live cd?"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by solotwit on 2009-06-25
I burned the .iso file as an image to disc. I put it in the drive and hit restart, but it doesn't run in gParted live cd.

---

### Post by keplerspeed on 2009-06-25
Check the md5sum, or just boot into ubuntu live cd, and go to system>admin>partition editor - same thing!

---

### Post by solotwit on 2009-06-25
okay, so "boot into ubuntu" means during the GRUB boot hit the esc key and choose cdrom drive as first boot. Got it.

---

### Post by keplerspeed on 2009-06-25
Well that would be the same method for the gparted live cd too.

---

### Post by lisati on 2009-06-25
> **solotwit said:**
> okay, so "boot into ubuntu" means during the GRUB boot hit the esc key and choose cdrom drive as first boot. Got it.

It can sometimes work better if you use the "Ubuntu Live CD" as  i.e. the Ubuntu installation disk, which has a copy of gParted on it. Boot from the CD and choose "try ubuntu without installing"

---

### Post by paul_be on 2009-06-25
You may also consider making the cd drive the first device in the boot order (bios) so you dont have to hit escape every time you boot from a cd.  Personal preference though

---

### Post by keplerspeed on 2009-06-25
Go into your bios settings, and you can modify the boot order or boot preference. BIOS menus vary, so have a bit of a look. You may have to press f12 or something instead of esc to open the BIOS menu.

I am seeing similar avatar - hah fooled me for a second!

---

### Post by balachandarlinks on 2009-06-25
Ya..there is no need to burn the gparted iso.Most of the ubuntu live CD's are bundled with gparted.So jus login with ubuntu live CD and use gparted. 
                  cheers....

---

