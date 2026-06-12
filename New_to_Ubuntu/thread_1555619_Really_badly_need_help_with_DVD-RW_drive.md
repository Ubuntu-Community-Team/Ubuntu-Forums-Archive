---
title: "Really badly need help with DVD-RW drive"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by John A on 2010-08-18
I really need help with this problem. I've put a DVD-RW disc in the drive, and try to burn an iso (Windows 7 64-bit) with Brasero  AND NOTHING HAPPENS :( :(. The DVD isn't being found. Please god help me.

---

### Post by Grenage on 2010-08-18
I presume you can read normal DVDs, and that it is in fact a DVD writer?  Give us as much information as possible.

---

### Post by harrisonk on 2010-08-18
Hello

First don't panic!

Second Have you ever taken apart your computer? It could be a loose wire somewhere.

If that isn't the problem, try a diferent disk, not all disks are detected equaly and make sure that the cd drive is detected. I don't know how to check that it is detected but someone else may.

Harrison

---

### Post by John A on 2010-08-18
> **Grenage said:**
> I presume you can read normal DVDs, and that it is in fact a DVD writer?  Give us as much information as possible.

> **harrisonk said:**
> Hello

First don't panic!

Second Have you ever taken apart your computer? It could be a loose wire somewhere.

If that isn't the problem, try a diferent disk, not all disks are detected equaly and make sure that the cd drive is detected. I don't know how to check that it is detected but someone else may.

Harrison

It can read DVD's fine,  and I have tried all my DVD-RW's. I'm sure it's a writer. It's whatever drive comes with a Dell Optiplex 745. I have checked the wires and they are fine.

---

### Post by Grenage on 2010-08-18
Have you ever written a disc with this drive, or has this problem only occurred recently (ubuntu install)?

---

### Post by John A on 2010-08-18
> **Grenage said:**
> Have you ever written a disc with this drive, or has this problem only occurred recently (ubuntu install)?

Yes I wrote alot of discs on Windows. This problem has occurred ever since I installed Ubuntu.

---

### Post by LowSky on 2010-08-18
Maybe nothing is happening because you are trying to burn an ISO of a proprietary operating system.

All joking aside. I'm on a Optiplex 745 and it does have a DVD-RW.

Have your tried writing other things to the DVD-RW, not just reading? Maybe try a new disk.

---

### Post by John A on 2010-08-18
> **LowSky said:**
> Maybe nothing is happening because you are trying to burn an ISO of a proprietary operating system.

All joking aside. I'm on a Optiplex 745 and it does have a DVD-RW.

Have your tried writing other things to the DVD-RW, not just reading? Maybe try a new disk.

I can't as the DVD-RW can't be found.

---

### Post by Sef on 2010-08-18
I changed to GnomeBaker for my burning needs; I have found that it works better than Brasero, the default burner.  It's available from the Ubuntu Software Center, if Universe is enabled.

---

### Post by davdo2004 on 2010-08-18
The best thing you can do is get shut of Brasero, install ktorrent from the repo and select burn image.

---

### Post by John A on 2010-08-18
> **Sef said:**
> I changed to GnomeBaker for my burning needs; I have found that it works better than Brasero, the default burner.  It's available from the Ubuntu Software Center, if Universe is enabled.

I just tried that software after reading your post. At no surprise, it failed after 2 seconds, spat the disc out and then gave me the following output:
:-( /dev/sr0: media is not recognized as recordable DVD: 10

---

### Post by Grenage on 2010-08-18
I think your DVD drive is knackered, but I could be wrong.

---

### Post by John A on 2010-08-18
> **Grenage said:**
> I think your DVD drive is knackered, but I could be wrong.

I don't understand how it could be broke. It plays DVD's and CD's fine, but nothing re-writeable.

---

### Post by Grenage on 2010-08-18
Reading a disc, and writing to a disc are different things.  I've seen many drives that would read a disc, but fail to burn.

---

### Post by MooPi on 2010-08-18
Try this ,open a terminal and type ```
sudo lshw -c cdrom
``` paste the output back here.

---

### Post by John A on 2010-08-18
> **MooPi said:**
> Try this ,open a terminal and type ```
sudo lshw -c cdrom
``` paste the output back here.

I don't think it worked. It came up CPUID, then it changed to PCI (sysfs) then it really quickly flashed SCSI and I'm sure it when I tried to print screen it flashed Frame Buffer.

---

### Post by spiky001 on 2010-08-18
Hi I have come across this problem I got round it by blanking the disc using nero on xp machine

---

### Post by JBAlaska on 2010-08-18
Have you formatted the dvd-rw disk? Also maybe just try a dvd-r.

---

### Post by John A on 2010-08-18
> **spiky001 said:**
> Hi I have come across this problem I got round it by blanking the disc using nero on xp machine

> **JBAlaska said:**
> Have you formatted the dvd-rw disk? Also maybe just try a dvd-r.

I don't have an XP machine.

I don't know if the disc is formatted. But I am unsure to how I can format if the disc cannot be read.

---

