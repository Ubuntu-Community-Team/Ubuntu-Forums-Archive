---
title: "I had to install ubuntu on the whole hard drive"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by DoubleZ711 on 2009-08-13
I had been having too many problems trying to dual boot, and I ended up having way to many extra partitions and I couldn't even get into windows, so the only thing I could do without having a guide on the internet was install ubuntu and replace the whole hard drive. It fixed everything, but I am really uncomfortable with ubuntu, everything just seems so complicated on it. So my question is this, since I only have one partition now, if I were to reinstall windows over ubuntu, would I get the grub error 22 again? Or is there an english version of a guide on how to make an extra partition for vista? Id prefer to just wipe ubuntu pff, but the guides are so damn complicated. I really hope reinstalling windows is the solution. Please help!

---

### Post by Tibuda on 2009-08-13
If you reinstall Windows, it will replace GRUB for his own bootloader.

---

### Post by NightwishFan on 2009-08-13
Just reinstall Windows, using a CD/DVD. Enjoy setting it up. You will not get grub errors though.

You should note, that Ubuntu uses a live cd. You could have browsed the web from there and not need to install on the entire disk.

If you want to try Ubuntu, I recommend using WUBI. WUBI installs Ubuntu on a virtual partition that boots like a normal system. There is no risk to Windows when you install with WUBI.

To use WUBI just insert an Ubuntu CD while you are running Windows. Then you can choose to "Install inside Windows". Setup is very easy.

Please ask if you need any help or have more specific issues.

---

### Post by arochester on 2009-08-13
I don't think that Windows will automatically overwrite the MBR... You need to "fix the MBR" which can be done a variety of ways. Google:fix mbr

---

### Post by Don1500 on 2009-08-13
If you do a complete reinstall of windows from the disks, it will rewrite the MBR.

---

### Post by philinux on 2009-08-13
> **arochester said:**
> I don't think that Windows will automatically overwrite the MBR... 

Yes it jolly well does.

---

### Post by NightwishFan on 2009-08-13
You can also fix the Windows bootloader from a Super Grub disk.

[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso)

---

### Post by ugm6hr on 2009-08-13
> **DoubleZ711 said:**
> It fixed everything

Sorry you had so much difficulty... But I find it amusing that wiping Windows and installing Ubuntu fixed everything 
:popcorn:

Seriously, though.  I would reiterate (almost) everyone else: installing Windows will *fix* everything back.  In fact, you could have just installed Windows instead of Ubuntu wehn things started to go wrong.

---

