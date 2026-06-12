---
title: "help deleting Ubuntu Remix from USB drive"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by south_coaster on 2009-04-16
I install Ubuntu Remix on my new MSI WIND a few days ago using a Corsair Mini USB drive. This morning I needed to backup some files so I deleted the operating system from the USB drive. I believe I have done this before with a standard Corsair USB drive. Anyway, with everything deleted, including /.trash the USB drive only shows 800 mb of space! It is supposed to be a 4Gig drive. Did I do something wrong? Or is it a problem with the USB drive?

---

### Post by halitech on 2009-04-16
use Gparted to remove the partition(s) and recreate a single 4gig partition. Basically when you created the bootable USB drive, it created a new partition that was 800meg in size

---

### Post by south_coaster on 2009-04-16
> **halitech said:**
> use Gparted to remove the partition(s) and recreate a single 4gig partition. Basically when you created the bootable USB drive, it created a new partition that was 800meg in size

THANK YOU! That worked and I was able to backup my files. Thanks for your help.

---

### Post by halitech on 2009-04-16
glad to hear that worked for you :)

---

