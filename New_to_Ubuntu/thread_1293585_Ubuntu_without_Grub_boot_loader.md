---
title: "Ubuntu without Grub boot loader????"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by ratman1 on 2009-10-17
Hi,

I am very new in linux so please try to be "basic" with me :)


I recently removed ubuntu from my portable hard drive, and then had grub loading problems.

Last time i tried to do this the grub files somehow got half installed on my internal hdd's mbr and half on the external portable hard drive. Because of that when i booted without the phd plugged in this would show:

Grub loading stage 1.5
error 22


I fixed that and now i am wondering if it is possible to install Ubuntu 9.04 on my portable hard drive (which i frequently take out and carry around with me) so that when it is plugged in Ubuntu will boot and when the portable hard drive is unplugged the windows dual boot screen will show? Btw, I currently have a windows vista and windows 7 dual boot.

I have had experience in running Ubuntu persistently, and that is what i *don't* want to do.

If i am not being clear enough just post in something and i will try to answer it.


Thanks in advance,

Ratman

---

### Post by LewRockwell on 2009-10-17
telling the installer to use the whole disk should work that way unless the installer finds other drives and other operating systems

then it will probably install grub on your primary boot drive in a repeat performance of your earlier difficulties

the very, Very, VERY easiest way to avoid this altogether is to disconnect your other hard drive(s) before attempting your installation on the portable hard drive

as always, your mileage may vary

.

---

### Post by mike555 on 2009-10-17
You can install Ubuntu to your external HD , but you should also install grub to it ............ it's the little "advanced" tab just before the "install" button ..... (Ubuntu needs a bootloader like grub or lilo to start)....... then when it's plugged in your computer will boot to it .. if your bios is set to boot to USB before the internal HD.


just to be clear .. you install grub to the external partition that your installing Ubuntu to.

---

### Post by ratman1 on 2009-10-17
And if it isn't plugged in i won't get error 22 like last time?

Just making sure, i have learnt not to trust all sources now!!!

---

### Post by ratman1 on 2009-10-18
> **LewRockwell said:**
> the very, Very, VERY easiest way to avoid this altogether is to disconnect your other hard drive(s) before attempting your installation on the portable hard drive
 
I can't really do that seeing as i am working on a laptop...   :(

---

### Post by PhilWig on 2009-10-18
Can you disable the internal drive with a bios option?
Phil

---

### Post by smileyguy on 2009-10-18
> **ratman1 said:**
> I can't really do that seeing as i am working on a laptop...   :(

Why can't you disconnec the laptop's hard drive? Is it because you've never done it on a laptop beofre? Should be even easier than a desktop PC. Usually you only need to unscrew one little screw to open a panel at the bottom of the laptop. They normally just slide right out.

---

### Post by ratman1 on 2009-10-18
> **PhilWig said:**
> Can you disable the internal drive with a bios option?
Phil

No idea... I don't think there is an option though

---

### Post by longtom on 2009-10-18
> **ratman1 said:**
> I can't really do that seeing as i am working on a laptop...   :(

If you are more comfortable on a desktop, than do it there.  Installed an Ubuntu mini install on a USB stick and it works just fine - on most PCs I tried it on.

---

### Post by K.Mandla on 2009-10-18
> **ratman1 said:**
> now i am wondering if it is possible to install Ubuntu 9.04 on my portable hard drive (which i frequently take out and carry around with me) so that when it is plugged in Ubuntu will boot and when the portable hard drive is unplugged the windows dual boot screen will show? Btw, I currently have a windows vista and windows 7 dual boot.
Yes, this should be possible, but I've never done it. Seems like the easiest way would be to use a machine that could boot from USB, because then Grub could be installed to the USB drive and Windows could just exist in its own little world on the hard drive.

If it won't boot straight from USB, then ... it gets complicated.

---

