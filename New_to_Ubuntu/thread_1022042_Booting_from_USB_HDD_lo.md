---
title: "Booting from USB HDD lo"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by kai.scorpio on 2008-12-26
I have installed kubuntu on my removable USB-HDD. It boots more or less normally, sometimes my USB is only detected if i plug it in after the POST

I removed my internal HDD during the install to avoid messing any of the things on them up. If they are kept removed, kubuntu loads fine. However, after re-attatching the internal drives, kubuntu doesn't load, it always loads (vista) directly from the internal HDD.

My guess is that the USB HDD is somehow telling the computer to load the first HDD, which before was the USB, but now is the internal one, because if i have a bootable cd inserted, it skips loading this, despite my boot order being USB>CD>HDD.

Either way, how do I get my computer to load linux from my USB?

Thanks for any help,
Kai

---

### Post by candtalan on 2008-12-26
A normal install does two things. It installs the system onto your target hard drive, and also it will re-arrange booting information within the boot sector of the active partition(drive) and this boot sector tells the bios where to find the installed system/s.

An install into a removable drive can be managed, however the complications of the various options  may not be easy for a newcomer.

Your windows drive will contain the boot sector information for the windows boot loader, and this will not include your ubuntu drive.

---

### Post by kai.scorpio on 2008-12-26
Sorry, I didn't quite get that :P. Maybe I wasn't clear enough with my original problem.

Kubuntu was installed while the internal HDD was unplugged. If the internal HDD is unplugged and I boot from my USB drive, it works fine.

However, as soon as I plug my internal HDD back in, booting from USB* results in me landing on my vista installation, which is on the internal HDD.

I'm not quite sure what's causeing this, but I think it's that the USB HDD is no longer the first HDD, the internal one is (I think). I don't know much about how the booting process works, but is there any way to set it to load from the third HDD (this is where kubuntu should be, 2 internal HDDs + the USB HDD). If it's not that simple please correct me :confused:.

*I'm assuming the system boots from the USB HDD in this case, as it skips booting from CDROM, and my boot order is set to USB>CDROM>internal HDD (I have a bootable CD inserted just to test this).

---

