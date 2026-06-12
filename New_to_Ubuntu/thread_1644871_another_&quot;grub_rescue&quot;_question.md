---
title: "another &quot;grub rescue&quot; question"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by avlnewby on 2010-12-13
I am stuck in grub rescue. Have read numerous post re: how to fix the problem but I seem to be having fundamental problems that aren't answered.

First: I have been dual booting Windows 7 starter and Ubuntu 10.04 without problems on Asus 1005HA via wubi. (This machine has two hard drives. Windows is on C and I put Ubuntu on D). When I made a live CD and tried to upgrade to 10.10 I ran into grub rescue. I know the problem is that grub doesn't know what partition to look into to find the boot loader; but neither do I!

Second:  I have an external CD/DVD drive. The solutions I have read about mention booting from Live CD. I turn the machine on, get the grub rescue prompt, the CD drive starts turning.... and nothing happens.  So can't boot from the live CD

Third:  None of the command line script that I've typed in is recognized. I always get "Unknown command..." Except when I typed in "ls" and got (hd0)in response.

I bought this cheap (in a good way) machine to learn on, so nothing of value is on it. Would be happy to erase everything and start from zero..."if I only had a brain." Help? Anyone?

---

### Post by Quackers on 2010-12-13
Try going into your bios settings and set the usb cd drive as first boot device (not the internal cd, if there is one) then see if the live cd can boot.

---

### Post by wilee-nilee on 2010-12-13
> **avlnewby said:**
> I am stuck in grub rescue. Have read numerous post re: how to fix the problem but I seem to be having fundamental problems that aren't answered.

First: I have been dual booting Windows 7 starter and Ubuntu 10.04 without problems on Asus 1005HA via wubi. (This machine has two hard drives. Windows is on C and I put Ubuntu on D). When I made a live CD and tried to upgrade to 10.10 I ran into grub rescue. I know the problem is that grub doesn't know what partition to look into to find the boot loader; but neither do I!

Second:  I have an external CD/DVD drive. The solutions I have read about mention booting from Live CD. I turn the machine on, get the grub rescue prompt, the CD drive starts turning.... and nothing happens.  So can't boot from the live CD

Third:  None of the command line script that I've typed in is recognized. I always get "Unknown command..." Except when I typed in "ls" and got (hd0)in response.

I bought this cheap (in a good way) machine to learn on, so nothing of value is on it. Would be happy to erase everything and start from zero..."if I only had a brain." Help? Anyone?

There is a key prompt to have a boot from menu outside the bios you will have to figure out what it is mine is f12 at powering on could be any really including the esc key. Look on Goggle with your computer model and per-session boot prompt.

Then if you booted in look at this thread, as you probably just need the MS bootloader put in the MBR master boot record or the Linux Lilo would work. 
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

