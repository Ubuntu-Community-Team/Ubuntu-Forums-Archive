---
title: "Ubuntu 8.04LTS fails to boot-up after login screen"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by suomalainen on 2010-03-12
Ubunteros,

Yesterday morning I attempted to boot up my system and was met with the three attached screen shots that I have attached for review.

Believe it or not this entire "process"  ran for over 24 hours. I got intel dual core E4500.

Anyway, just moments ago I checked my PC and it appears to be trying to load the desktop. 

I don't know what the attachments I have included mean but assume that probably I need to reinstall Ubuntu?

Regardless, The biggest thing I would like to know and understand at this point is how can I salvage/retreive my email....????

If anything this is the only thing that matters to me.

Thanks everyone...

---

### Post by achase79 on 2010-03-12
I get this on one of my older computers, especially after a hard shutoff/power failure.  I am usually sent to busybox in which I try to mount the partition again (I think it fixes the ext3 journal) and then it restarts fine.

---

### Post by suomalainen on 2010-03-12
I haven't had any power failures and this isn't the first time that this has happened. The first time was about month and half ago....

But saving my e-mail is important to me. Any advice would be appreciated.

---

### Post by markbuntu on 2010-03-12
Do you have a live cd or usb stick?
can you boot from that?
Can you see your hard drive from there?

---

### Post by suomalainen on 2010-03-12
I can boot the live CD and also see my hard drive...

Can I get my email from here????

---

### Post by markbuntu on 2010-03-13
You can recover your email from the hard drive. If you are using evolution for your email client it will be in /home/username/.evolution/mail/local. It is a hidden directory.

Does this happen after the grub screen or before?
If you can get the grub menu you can try booting into the recovery kernel and try the fix broken packages option. You can also try booting into a previous kernel.

---

### Post by suomalainen on 2010-03-13
I tried booting a previous kernel and nothing worked for me.

---

### Post by louieb on 2010-03-13
After you get whatever you need copied off or if you find you can't browse the partition(s) with the Ubuntu install:
Something to try

Use the live cd - System>administration>partition editor

right click on the partition and select check then click apply - this will run fsck. and just might fix whatever went wrong.

---

### Post by suomalainen on 2010-03-14
Hi louieb!!!

Using the live cd - System>administration>partition editor

and formatting the defective drive do you know if this will delete everything and leave the HDD like a factory new hard drive???

Also, When formatting with Partition Editor does it know where BAD SECTORS are on a disk and mark them so Ubuntu doesn't try to use them???

Thank you for your support.

---

### Post by louieb on 2010-03-14
Formating the drive will not fix or mark bad sectors -  modern hard drives are self monitoring - from the [Bad block HOWTO for smartmontools]("http://smartmontools.sourceforge.net/badblockhowto.html")

> Handling bad blocks is a difficult problem as it often involves decisions about losing information. Modern storage devices tend to handle the simple cases automatically, for example by writing a disk sector that was read with difficulty to another area on the media. Even though such a remapping can be done by a disk drive transparently, there is still a lingering worry about media deterioration and the disk running out of spare sectors to remap. 

> I haven't had any power failures and this isn't the first time that this has happened. 

The [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") has the program that will check the smart status of the drive. 
Kind of sounds like the drive is going bad - thinks the next thing I would do is use the parted magic cd and check its status. - and start looking around for a replacement.

---

