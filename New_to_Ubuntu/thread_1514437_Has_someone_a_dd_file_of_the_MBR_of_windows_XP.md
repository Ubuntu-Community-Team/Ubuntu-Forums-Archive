---
title: "Has someone a dd file of the MBR of windows XP?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-06-21
Hello,

I need to remove the Grub on a PC for letting users use windows XP.

Has someone a file of the MBR ,. equivalent into removing grub, of windows?

---

### Post by dim3000 on 2010-06-21
> **frenchn00b said:**
> Hello,

I need to remove the Grub on a PC for letting users use windows XP.

Has someone a file of the MBR ,. equivalent into removing grub, of windows?

Even if someone did and it was possible to use it, i'm pretty sure that's illegal to transfer or copy.

---

### Post by wilee-nilee on 2010-06-21
> **frenchn00b said:**
> Hello,

I need to remove the Grub on a PC for letting users use windows XP.

Has someone a file of the MBR ,. equivalent into removing grub, of windows?
download this slipstream if you don't have a XP iso , burn it and run fixmbr in the repair.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Here is a link that explains the process.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by Serpher on 2010-06-21
> **dim3000 said:**
> Even if someone did and it was possible to use it, i'm pretty sure that's illegal to transfer or copy.

GRUB and almost everything Linux is open source. There's nothing illegal about it, no Microsoft binaries are being asked for.

---

### Post by dim3000 on 2010-06-21
> **Sepher]no Microsoft binaries are being asked for.[/QUOTE]

[QUOTE=frenchn00b said:**
> Has someone a file of the MBR ,. equivalent into removing grub, of windows?

I'm pretty sure the words, "has someone a file of the MBR of windows" are synonymous with asking for Microsoft binaries.

---

### Post by fourscore on 2010-06-21
I don't quite follow your query.   Are u having a dualboot system. If so the Grub must be configured to also boot into XP as an option.

Anyway check out the following links for restoring the MBR.
- [http://www.blogmanno.com/?q=node/9](http://www.blogmanno.com/?q=node/9)
- [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

Pls note that once you repair/restore the MBR you will not be able to get into Ubuntu.  You will need to reinstall GRUB.

---

### Post by 3rdalbum on 2010-06-21
Funnily enough, copying an MBR is appaently illegal.

There is a program called MS-SYS that you can compile, that creates a valid MBR. It is no longer in the Ubuntu repos but if you compile it in the live CD environment you can use it.

---

### Post by Metrop021 on 2010-06-21
> **dim3000 said:**
> Even if someone did and it was possible to use it, i'm pretty sure that's illegal to transfer or copy.

frankly since when has that stopped anybody

---

### Post by Paul T. on 2010-06-21
> **frenchn00b said:**
> Hello,

I need to remove the Grub on a PC for letting users use windows XP.

Has someone a file of the MBR ,. equivalent into removing grub, of windows?

It's possible to re-build the MBR by booting from the XP CD and selecting the 'repair' option.

---

### Post by wilee-nilee on 2010-06-21
> **Paul T. said:**
> It's possible to re-build the MBR by booting from the XP CD and selecting the 'repair' option.

Yes, but the right files have to be in XP for it to work.
If you need more help start a thread list whats going on and post the bootscript in my signature in code tags.  These files are needed in the XP partition.
```
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```

If XP was working they are probably still there, but if you want to protect your system run the script for your self and look for this line in XP.

---

### Post by dim3000 on 2010-06-21
> **Metrop021 said:**
> frankly since when has that stopped anybody

When I say transfer I mean me giving my MBR to you, not you using and copying your own MBR.

And Windows MBR problems shouldn't even be on a Ubuntu forum. I when if it wasn't Windows MBR but GRUB that you were copying you wouldn't go to the Microsoft Support Forums and ask there would you? They'd tell you go to the Ubuntu forums.

Well this is the opposite, so i'm saying to the OP go to the Windows Forums.

---

### Post by tacotime on 2010-06-21
Just pop in your install cd and run a fix mbr

here's a forum about that-
[http://www.techzonez.com/forums/showthread.php?t=3975](http://www.techzonez.com/forums/showthread.php?t=3975)

---

### Post by tacotime on 2010-06-21
> **Metrop021 said:**
> frankly since when has that stopped anybody

True- normally it doesn't :lolflag:

---

### Post by oldfred on 2010-06-21
All the windows boot loader does is scan the partition table for the active partition (boot flag) and jump to it to continue booting. Lilo uses the same process.

per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

