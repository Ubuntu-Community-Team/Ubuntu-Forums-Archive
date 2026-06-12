---
title: "How do I install it?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by corncob on 2009-08-04
After Eeebuntu crashed on my eeepc1000 (the Xandros that came with it is still working) I downloaded ubuntu-9.04-netbook-remix-i386.img.  I copied it to a DVD, a pen drive, and an SD card but I have been unable to get it to boot from any of these devices.  Is the something I must do to this file to make it bootable?  I downloaded it to and copied it from my eeebox running Ubuntu Ultimate 2.0, incidently.

---

### Post by kansasnoob on 2009-08-04
> **corncob said:**
> After Eeebuntu crashed on my eeepc1000 (the Xandros that came with it is still working) I downloaded ubuntu-9.04-netbook-remix-i386.img.  I copied it to a DVD, a pen drive, and an SD card but I have been unable to get it to boot from any of these devices.  Is the something I must do to this file to make it bootable?  I downloaded it to and copied it from my eeebox running Ubuntu Ultimate 2.0, incidently.

So you have been able to run other live CD's/DVD's on the same machine?

Did you check the md5sum of the download and/or burn?

---

### Post by snakeman21 on 2009-08-04
They should really make this a sticky... I've answered it at least 5 or 6 times on various threads... Here we go...

For some reason, USB Startup Disk Creator will not work for putting Netbook Remix on a flash drive for installation.  Instead, download USB ImageWriter and use that.  I don't know why, but for whatever reason, it works.  Good Luck!  Get USB ImageWriter from synaptic package manager.

---

### Post by corncob on 2009-08-05
> **snakeman21 said:**
> They should really make this a sticky... I've answered it at least 5 or 6 times on various threads... Here we go...

For some reason, USB Startup Disk Creator will not work for putting Netbook Remix on a flash drive for installation.  Instead, download USB ImageWriter and use that.  I don't know why, but for whatever reason, it works.  Good Luck!  Get USB ImageWriter from synaptic package manager.

Thank you!  I did think that the contents of the img file, not the file itself, should be copied to the boot device but cd writer just wasn't doing it (although it worked with iso files in the past).  Jaunty NBR is now installed on sdb (Xandros remains on sda) with just one problem:  Grub is installed on sdb and not the boot partition.  I really do know better than this, honest, but I don't remember it giving me a choice.  Is there any way to move it without reinstalling Jaunty?  I haven't searched the forum yet -- just asking while I'm here.

---

### Post by gordintoronto on 2009-08-05
> **corncob said:**
> Thank you!  I did think that the contents of the img file, not the file itself, should be copied to the boot device but cd writer just wasn't doing it (although it worked with iso files in the past).

If you start Brasero from the Application menu, it will offer a "burn image" option.  For some reason, it doesn't do that if you run it from the "you just inserted a blank CD" dialogue.

---

### Post by corncob on 2009-08-05
> **gordintoronto said:**
> If you start Brasero from the Application menu, it will offer a "burn image" option.  For some reason, it doesn't do that if you run it from the "you just inserted a blank CD" dialogue.

Good Info!

For moving Grub I found instructions at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) .  I'll try that in the morning.

---

