---
title: "Ubuntu errors? Or is it my Hardware?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Naesen on 2009-02-28
So I successfully installed Ubuntu (I have switched to it from Windows XP, have both OS on my computer.) and am able to load it, etc. However, I am experiencing two major errors that I cannot determine to be hardware or Ubuntu related: The first, is what I can describe as a "redraw error."  A little square of previous background always seems to stay around my mouse.  It doesn't really hinder me, I just would like to know if there's a way to fix it.  Second, whenever I try to update or open the terminal all I am able to see is a white box in place of what I am looking to open (included is a picture of both problems).  I would like to know if this is resolvable through Ubuntu or is it the fault of my computer's 8-year old hardware? (single core 1.3 Ghz processor, Intel graphics processor (integrated), 512 MB RAM)

---

### Post by Kevbert on 2009-02-28
Welcome to Ubuntu.
How did you install Ubuntu, did you burn your own CD (from a downloaded ISO) or get a pre-burnt CD ?
Have you checked the ISO checksum/[[COLOR="Red"]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") ?  
Have you checked the CD integrity (via the CD boot menu prior to installing) ?
Have you run memtest from the boot menu ?

---

### Post by Naesen on 2009-02-28
> **Kevbert said:**
> Welcome to Ubuntu.
How did you install Ubuntu, did you burn your own CD (from a downloaded ISO) or get a pre-burnt CD ?
Have you checked the ISO checksum/[[COLOR="Red"]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") ?  
Have you checked the CD integrity (via the CD boot menu prior to installing) ?
Have you run memtest from the boot menu ?

I actually didn't do it via CD, I saved everything to a Flash Drive and then installed it directly to my hard drive from there (via the setup provided for windows machines.) I rebooted, etc, and it installed from the drive, and then I was able to load into Ubuntu (it's version 8.10 by the way). The games work fine, but it really looks like a graphics error, and I honestly wouldn't be surprised if my onboard card is shot, except that Windows works fine.  I haven't done the checksum, I'll do that and yield the results.

---

### Post by Kevbert on 2009-03-01
It's also worth running memtest as you can run Windows with faulty memory (but it may crash occasionally for no apparent reason).
It's possible that the graphics driver may be wrong. If you go to System-Administration-Hardware Drivers, see if it gives you the option of installing a graphics driver for your PC.

---

### Post by clive littlewood on 2009-03-01
Hi

Sounds like a graphics card driver problem to me.

Have you checked for drivers in System > Admin > Hardware Drivers.

If you know your graphics card google for drivers + Ubuntu

And we can take it from there.

Clive

---

