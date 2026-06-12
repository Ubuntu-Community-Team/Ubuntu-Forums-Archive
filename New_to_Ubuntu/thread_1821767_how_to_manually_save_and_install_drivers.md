---
title: "how to manually save and install drivers?"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by goodbye-windows(tm) on 2011-08-09
Hi All,

I need an mp3 codec for my other desktop computer (xubuntu), which does not have an internet connection. 

In the software center, there is no option to save drivers so they can be transferred to a memory stick and loaded onto a non internet capable system.

I only need an mp3 codec.

How do I download and archive an mp3 codec so it can be installed via a usb memory module?

TIA.

Art

---

### Post by gandaran on 2011-08-09
> **goodbye-windoze said:**
> Hi All,

I need an mp3 codec for my other desktop computer (xubuntu), which does not have an internet connection. 

In the software center, there is no option to save drivers so they can be transferred to a memory stick and loaded onto a non internet capable system.

I only need an mp3 codec.

How do I download and archive an mp3 codec so it can be installed via a usb memory module?

TIA.

Art
all packages are saved until you remove them (sudo apt-get clean)
you can get all packages downloaded on one ubuntu system from /var/cache/apt/archives and just copy them (all or just the ones you need) to the same location on the other computer using the pen drive, then mark for install on the software center

---

### Post by SavageWolf on 2011-08-09
You can also use "APTOnCD", which should do this.

---

### Post by goodbye-windows(tm) on 2011-08-10
Wow, that's awesome, tnx!!!

It looks like I can use an archive of that folder to quickly bring my desktop software up to the same level as my laptop without having to download everything again!!!

Is there a similar method for applying security updates? My laptop is fully updated, but the desktop has never been updated as it does not have internet access. 

Regards,

Art

---

