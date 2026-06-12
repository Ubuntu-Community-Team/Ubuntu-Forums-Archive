---
title: "Creating Bootable USB Vista"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by baiserabies on 2009-04-09
ok, so i im running ubuntu right now with no dual boot to windows, and i currently need windows back,
i tried using a bootable copy of xp, but for some odd reason it didnt read my harddrive so i wouldnt install.
When i went to boot from a vista dvd, it just boot straight to the harddrive (linux)
My computer (hp pavillion pv6000) boots from cds but not dvds..

So what i wanted to know is if there is anyway to create a bootable usb drive of windows vista from a computer running linux

---

### Post by wolfen69 on 2009-04-09
> **baiserabies said:**
> 
i tried using a bootable copy of xp, but for some odd reason it didnt read my harddrive so i wouldnt install.


that's probably because you are using a sata drive. xp retail discs do not have sata drivers. go to the manufacturers website and download the sata drivers onto a floppy disc. then when you begin installation of xp, press F6 when prompted and load the sata drivers.

---

### Post by stchman on 2009-04-09
> **baiserabies said:**
> ok, so i im running ubuntu right now with no dual boot to windows, and i currently need windows back,
i tried using a bootable copy of xp, but for some odd reason it didnt read my harddrive so i wouldnt install.
When i went to boot from a vista dvd, it just boot straight to the harddrive (linux)
My computer (hp pavillion pv6000) boots from cds but not dvds..

So what i wanted to know is if there is anyway to create a bootable usb drive of windows vista from a computer running linux

There is a thing called BartPE disc.  The reason XP could not read your disc was that XP has no SATA drivers built in.

When it comes to usability Ubuntu LiveCD far surpasses anything Windows has to offer.

---

### Post by The Cog on 2009-04-09
Perhaps you could install windows inside VirtualBox, running under Ubuntu? That's what I do when I need to run a windows-only program. VirtualBox is avaiilable in the repositories.

---

