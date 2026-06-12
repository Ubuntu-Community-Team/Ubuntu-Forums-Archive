---
title: "Can't save large files to external hdd"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by griz on 2009-01-31
Hi all,

I know that I'm missing something really simple here, but just can't figure it out.  Bought a new WD Elements 1T external hdd, but can't seem to be able to save large files (eg., .iso files of around 4.4g) to it.  Everything else seems to work fine and even have problems when I try to rip a dvd to it.  Any suggestions please.

Paul.

---

### Post by taurus on 2009-01-31
If your external harddrive is formatted as fat32/vfat, then you would not be able to save anything to it larger than 4GB.  If you plan to have something larger than 4GB, you have to format it to ntfs.

---

### Post by griz on 2009-01-31
Thanks for that Taurus,

Guess I might even change it to ext3, probably a better option.  I should have thought of that myself, just too tired I guess lol.

---

### Post by jimmy the saint on 2009-01-31
In fact, unless you plan on sharing the drive with a windows box, you can format it to ext3, just like the linux partition.

---

### Post by niteshifter on 2009-01-31
> **jimmy the saint said:**
> In fact, unless you plan on sharing the drive with a windows box, you can format it to ext3, just like the linux partition.

Just to clarify the above, we're kinda overloading the term "share" here:

If you wish to share the drive with a windows box _over a network connection_ (serve it via Samba) you can format it however you like (ext3, RieserFS, etc.)

If you wish to _connect it directly_ to a windows box (USB / Firewire) then FAT32 / NTFS are what windows understands natively.

---

### Post by griz on 2009-01-31
It will most likely only be shared over a network, so I'm thinking RieserFS.  My understanding is that's the best file system to use.  Am I right in that assumption?

---

### Post by stderr on 2009-01-31
Depends on many things including average file size. Just google Linux filesystems to learn more. Good luck!

---

### Post by griz on 2009-01-31
Thanks very much everyone.  Have reformatted to ReiserFS and everything is working fine.

---

### Post by gillmt on 2009-02-08
Hi Jimmy the saint. I tried to format my USB HDD to ext 3 with Pertition Manager on Ibex - got an error message. Do you know what might cause this please?

---

### Post by taurus on 2009-02-08
> **gillmt said:**
> Hi Jimmy the saint. I tried to format my USB HDD to ext 3 with Pertition Manager on Ibex - got an error message. Do you know what might cause this please?

Do you want to share that error message?  Make sure the drive is not mounted before you format it.

---

### Post by halitech on 2009-02-08
might be able to help better with the error message ;)

was the drive mounted when you tried to format it?

---

