---
title: "What the hell happened ?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-02-14
I don't know what happened.Maybe you guys can help.I was trying to get my laptop's wireless running for some blue-tooth transfer.I enabled broad-com sta something driver(I don't remember but it was  there in the hardware drivers' list so I enabled it.
It demanded a restart , after the restart the grub loaded properly , I selected Ubuntu (as usual) after a couple of seconds what I get is this :
> [linux - bzImage , setup = 0x3400 , 867446 size=0x3b26e0]
[Initrd , addr=0x37865000 size=0x78a84f]
Kernel Panic-not syncing :VFS:Unable to mount root fs on unknown block(8,2)
And its stuck on this...
Help

---

### Post by Satoru-san on 2010-02-14
Do you have any older kernels that you can boot in grub? If not I will tell you how to boot the livecd and chroot.

---

### Post by peace.gangsta on 2010-02-14
> **Satoru-san said:**
> Do you have any older kernels that you can boot in grub? If not I will tell you how to boot the livecd and chroot.
the grub shows only .14 kernel and a recovery mode and windows(/dev/sda) one

---

### Post by Satoru-san on 2010-02-14
wow, you dont even have the .17 kernel. Try booting recovery mode, I dont exactly know what it does but maybe it will give you a terminal that we can fix from.

---

### Post by peace.gangsta on 2010-02-14
> **Satoru-san said:**
> wow, you dont even have the .17 kernel. Try booting recovery mode, I dont exactly know what it does but maybe it will give you a terminal that we can fix from.
I haven't upgraded in a while
Well I ll see right away

---

