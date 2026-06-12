---
title: "Live cd problem"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by anchorschmidt on 2009-04-12
I want to partition my drives and I inserted the Ubuntu live cd and restarted my system (I had the disk checked by md5) but in the boot menu where I have to select what to boot from, there is no option there where I can boot from cd: there are only two sets of Ubuntu kernels with recovery modes and a memtest but nothing else.

---

### Post by drowner on 2009-04-12
> **anchorschmidt said:**
> I want to partition my drives and I inserted the Ubuntu live cd and restarted my system (I had the disk checked by md5) but in the boot menu where I have to select what to boot from, there is no option there where I can boot from cd: there are only two sets of Ubuntu kernels with recovery modes and a memtest but nothing else.

The option to boot from CD is not one made by the boot manager on your hard drive, it is made earlier than that - by BIOS.

So, BIOS says boot from hard drive, then you get the option which kernel or memtest.

Do you know how to change your BIOS boot loading settings?

---

### Post by Paqman on 2009-04-12
You need to set your BIOS to boot from CD. You'll need to press a button right at the start of the boot. It varies from machine to machine, but normally Del, F2, something like that. It should flash up when it starts to boot what you need to press.

Then change your boot order so that the CD comes before the hard drive.

---

