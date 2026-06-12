---
title: "I may have just effed my computer..."
date: 2011-05-31
forum: New to Ubuntu
---

### Post by iBurley on 2011-05-31
Alright guys, I need some serious help with this one. :(

I messed up my Windows install, so I wiped it and but Ubuntu 11.04 on it. This morning, I went to reinstall Windows 7 on it, and during the installation I wiped all of my partitions, but then I got an error before I could install Windows.

Now, when I try to boot to one of my flash drives to install either Windows or Linux, I can't even get far enough to go into boot menu or bios to change boot order. As soon as I get my splash screen, it goes to an all black screen with white text and at the bottom, it says:

GRUB error: unknown filesystem.
grub rescue>

WHAT DO I DO NOW?!?

Anybody that can help, please do, I am at a loss.

Thanks guys!

---

### Post by eriktheblu on 2011-05-31
If it's telling you grub, you missed the BIOS.

If you can get into the BIOS (press the key faster/sooner?) change the boot order.

Failing that check to see that your install media is actually bootable. Check by disconnecting your internal disk with the install media in place. If it fails to boot, then that is likely the problem.

Edit to add: The Grub message means that your MBR pointed to a partition where it expected to find Grub, but Grub was not there (due to the previously mentioned format)

---

### Post by iBurley on 2011-05-31
Well I know they're both bootable, that's what I used to install Ubuntu and then what I used to attempt my Windows install. Both booted fine. I'll go try hitting the button as soon as I power on, but I don't think I mis it, I think it just skips that part. Thank you for reply though.

---

### Post by iBurley on 2011-05-31
Alright, I think I got it. It appears that the problem was my keyboard (somehow?). I noticed on that last boot that no lights on the keyboard were lighting, I fiddled with the plug and messed with some buttons and upon next boot, they flashed and I got bios. I'm attempting the Windows install again but if it fails again I'll just post an update. First, though, I'll see if I can throw Ubuntu back on there (if the Windows one fails).

---

### Post by iBurley on 2011-05-31
And I got it! Windows is up and running! Now, if I did choose to dual boot with Ubuntu, can anybody confirm that this process works with 11.04:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by alphacrucis2 on 2011-05-31
> **iBurley said:**
> And I got it! Windows is up and running! Now, if I did choose to dual boot with Ubuntu, can anybody confirm that this process works with 11.04:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Yes it does as long as you have enough unallocated space to create at least one partition for ubuntu. It isn't necessary but very useful to set up two partitions namely a partition for the file system root / and another separate partition for /home. You may also want a swap partition matching the size of your RAM.

---

