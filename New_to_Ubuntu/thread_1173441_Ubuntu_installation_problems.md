---
title: "Ubuntu installation problems"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Reckers on 2009-05-29
WARNING: I'm a bit of a NOOB.

I just got a new hard drive (Western Digital, 500 GB, 5400 RPM) and put Ubuntu to duel boot.

Last time I tried this, on the old, corrupted hard drive, I experienced some flaw where everytime I try to start my computer up cold it reaches the "Grub Loading Stage 1.5." point and freezes.  Only on the third start up, and it is always the third time, does it reach the boot screen.

As you can probably imagine, that gets old fast.  Any idea what such is happening?

Secondly, and this is somewhat petty, is there a way that Vista can be the default OS to boot too?  Such that when I don't hit a key after ten seconds, Vista is the OS it boots to?

Thanks.

---

### Post by NESFreak on 2009-05-29
> **Reckers said:**
> WARNING: I'm a bit of a NOOB.

I just got a new hard drive (Western Digital, 500 GB, 5400 RPM) and put Ubuntu to duel boot.

Last time I tried this, on the old, corrupted hard drive, I experienced some flaw where everytime I try to start my computer up cold it reaches the "Grub Loading Stage 1.5." point and freezes.  Only on the third start up, and it is always the third time, does it reach the boot screen.

As you can probably imagine, that gets old fast.  Any idea what such is happening?

Secondly, and this is somewhat petty, is there a way that Vista can be the default OS to boot too?  Such that when I don't hit a key after ten seconds, Vista is the OS it boots to?

Thanks.

dont know why, but for setting grub to default to windows, have a look here:
[https://help.ubuntu.com/community/GrubHowto/](https://help.ubuntu.com/community/GrubHowto/)
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by Origin415 on 2009-05-29
I don't know about your main problem, but to change the default OS, do

```
sudo gedit /boot/grub/menu.lst
```

and look for the line that says
> default *n*
(n being a number, it should be near the top of the file)

Change that number to the number of the OS you want to boot to, where the first in the list is 0, the next 1, and so on, and save it.

Edit: guess I was beaten to it. :]

---

### Post by Hospadar on 2009-05-29
> **Reckers said:**
> ... and put Ubuntu to duel boot.
There's no need to have your OS's fighting now =)

as to the problem with the old drive, had you ever tried re-installing grub (or ubuntu)  you may have just had a bad install or something weird with the partition.  I had this weird problem on an old laptop I used for a digital picture frame where I had to boot it twice because it tried to check the disk and failed on the first attempt.

---

### Post by Reckers on 2009-06-03
Thanks!

After I reinstalled Ubuntu, that worked perfectly.

---

