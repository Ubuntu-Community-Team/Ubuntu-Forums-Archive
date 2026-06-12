---
title: "W7 RC Install"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-05-08
HI all,
Just wondering how I can install W7 release candidate without scrubbing my grub :(

TFC!
Robin

---

### Post by MysticalRiotCandy on 2009-05-08
Unfortunately, installing Windows (any version) will install Microsoft's bootloader to the MBR, quite rudely overwriting anything else that was in there.  Meaning GRUB.  The best way to get around this is to just install Windows in a separate partition, then loading up a LiveCD of Ubuntu and fixing your MBR for Ubuntu on that.  Use this tutorial on that; it should do the trick, even though it's a bit old.

---

### Post by lovinglinux on 2009-05-08
Restoring the grub is not complicated. I was afraid at first, but everything went pretty well. I followed [this tutorial](http://ubuntuforums.org/showthread.php?t=224351).

After restoring the grub you won't be able to boot into Windows. You need to edit the [/boot/grub/menu.lst](http://www.google.com/search?q=/boot/grub/menu.lst+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) file to include Windows.

---

### Post by hungryOrb on 2009-05-08
Thanks Guys :D

---

### Post by wizard10000 on 2009-05-08
Run it in a VM - that's what I did.

---

### Post by hungryOrb on 2009-05-08
> **wizard10000 said:**
> Run it in a VM - that's what I did.

Nice idea but, not magical :(

BTW, is there any important note to creating partitions? Can I let the Windows 7 installer create partitions for me?

---

### Post by kanikilu on 2009-05-08
> **hungryOrb said:**
> Nice idea but, not magical :(

BTW, is there any important note to creating partitions? Can I let the Windows 7 installer create partitions for me? Only if the Win7 installer can non-destructively resize linux partitions - which I'm *guessing* it can't.

I would use an Ubuntu Live CD (or GParted Live CD) to run GParted and resize your existing partitions (if needed) and create a new NTFS partition for Windows.

GParted should be able to resize without destroying data, but always backup before changing the partitions!

---

### Post by billgoldberg on 2009-05-08
> **lovinglinux said:**
> Restoring the grub is not complicated. I was afraid at first, but everything went pretty well. I followed [this tutorial](http://ubuntuforums.org/showthread.php?t=224351).

After restoring the grub you won't be able to boot into Windows. You need to edit the [/boot/grub/menu.lst](http://www.google.com/search?q=/boot/grub/menu.lst+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) file to include Windows.

I had quite some problems restoring grub after installing W7RC1.

I finally gave up and ran the installer again, without formatting my / and that put grub back and left my system intact.

---

### Post by hungryOrb on 2009-05-08
thanks for suggestions :D

BGB, Can I ask, what installer did you run again? Not sure I understand your predicament. If the MBR was replaced, why is it difficult to simply restore with a grub setup? Does windows try to damage grub ? ://

---

