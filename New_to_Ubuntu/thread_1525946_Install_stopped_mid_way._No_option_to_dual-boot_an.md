---
title: "Install stopped mid way. No option to dual-boot anymore."
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Neo-Dragon on 2010-07-07
Hey guys.
I completely edited this thread as I have a new problem.
I think I got Ubuntu 10.04 to install fine, but I am stuck on boot.
I get a black screen saying:
Booting from local disk...
error: no such device:
grub rescue.

How do I sort this out?

Cheers.

**Edit: **
I installed ubuntu to an external drive I believe. 
I can't boot into Windows or unbuntu, and my wireless connections won't work.
I can't find any wireless connections at all.
So I'm on my laptop.

---

### Post by Rubi1200 on 2010-07-07
> **Neo-Dragon said:**
> Hey guys.
I completely edited this thread as I have a new problem.
I think I got Ubuntu 10.04 to install fine, but I am stuck on boot.
I get a black screen saying:
Booting from local disk...
error: no such device:
grub rescue.

How do I sort this out?

Cheers.

If you still have the Ubuntu CD (I am assuming this is a normal install and not via Wubi?) then boot the computer choosing the option to try in live mode **not** install.

Once you are in, click on the link at the bottom of my post and follow the instructions there before posting the results back here.

---

### Post by Neo-Dragon on 2010-07-07
I'm sorry, but I'm such a beginner at this.
I installed via USB.
I installed it to the External Harddrive, so this is the problem right?

I can't boot into either Windows or Ubuntu at all now.

---

### Post by Rubi1200 on 2010-07-07
> **Neo-Dragon said:**
> I'm sorry, but I'm such a beginner at this.
I installed via USB.
I installed it to the External Harddrive, so this is the problem right?

I can't boot into either Windows or Ubuntu at all now.

>  I installed it to the External Harddrive, so this is the problem right?

Possibly; I suspect GRUB has been incorrectly installed, which is why we need the results of the bootscript.

Let's see; are you connected to the computer now using the USB

The option is still to do as I suggested before:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please post the results using the code tag #

---

### Post by bcbc on 2010-07-07
This happened to me, you boot from usb to install ubuntu (usb is /dev/sdb) then you plug in an external (/dev/sdc) and install ubuntu. Grub is placed on /dev/sda.

You remove the boot usb, and your external becomes /dev/sdb.... and grub won't find it. So you are hooped.

You can try (from the grub> prompt):
```
search.file /boot/grub/grub.cfg
```
then load it (assuming the first command returned (hd1,1)
```
configfile (hd1,1)/boot/grub/grub.cfg
```

then edit the first entry (press 'e') and change hd2 to hd1 and /dev/sdc to /dev/sdb. Then CTRL+X

When you're in Ubuntu run:
```
sudo update-grub
```
You could reinstall grub2 to /dev/sda and it will work - but only when the external is plugged in. Better to reinstall the windows boot loader (or equivalent e.g. lilo) to /dev/sda and grub2 to /dev/sdb and then boot from the usb whenever you want ubuntu.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo grub-install /dev/sdb

```

Or you could try and repair it from a live USB, but trying to boot from usb and then doing the fix might result in the same prob unless you create and edit the device map first. You would do better to use a live CD in this case.

---

