---
title: "Broadcom (Surprise Surprise) with Compaq Presario V6000"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by crthomas on 2007-02-12
I killed X11 with the kernel update, and didn't think to check here for a fix, before I just reinstalled.  I can't get ndiswrapper to work.  I followed this: [http://ubuntuforums.org/showthread.php?t=286924](http://ubuntuforums.org/showthread.php?t=286924)
but it isn't working.  Ndiswrapper is installed, ndiswrapper -l says the hardware is present, and its listed in lsmod.

---

### Post by crthomas on 2007-02-12
I forgot to mention, in order to get the machine to boot, I have to use either pci=noacpi or acpi=off in the grub menu.  I don't know if this is affecting it or not, but acpi=off kept some stuff from working.

---

### Post by crthomas on 2007-02-12
I used automatix to install the graphical ndiswrapper utility, and it said the hardware wasn't present.  It said before that the driver was installed, not that the hardware was present.

---

### Post by crthomas on 2007-02-12
Okay, I finally got ndiswrapper to show that the driver was installed AND the hardware is present, but it still didn't do anything.

---

### Post by crthomas on 2007-02-13
Fixed it myself.  I think there might be some bad hardware in this laptop, because I reinstalled AGAIN, and it worked this time, even though I didn't change anything.

---

### Post by yurtboy on 2007-02-13
could you share your menu.lst from grub and your xorg if it is all still working

---

### Post by crthomas on 2007-02-14
It started working without making changes to grub, so it is still the default.  Also, I haven't made any changes to the X11 config.  The installer for the nvidia drivers messed with it, and I can post it later, if you want, but there isn't anything special in there.

---

### Post by Noobie1982 on 2007-10-21
Hi,

I also have a presario v6000 that I'm trying to install gibbon (7.10) onto.  On install it recognises the wireless card exists but can't use it, so I followed the howto guide shown by the OP, and it simply refuses to work.  ndiswrapper reports the driver installed and the hardware present, but i don't think it's creating a device in the device management system, so although the software interface (ndiswrapper) is certain it exists and is working, the actual link from the kernel to the hardware doesn't seem to work.

I'm going to try the alternative in [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) tomorrow and see if I get any further joy with the 43xx driver, which I'm convinced is a better bet than trying to use the windows driver (bcmwl5).

The truly aggravating thing is that the v6000 has no PCMCIA slot so I can't even use a card with a known working chip (such as a dlink card), which I'm happy to fork out for, but I refuse to use a USB wireless dongle having had to admin networks with those things.

So, question to the OP, did ndiswrapper solve the issue for you or did you have to do something more tricky?

---

