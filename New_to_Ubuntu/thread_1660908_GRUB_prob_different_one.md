---
title: "GRUB prob different one"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by xcorpion on 2011-01-06
hi
i just step in
i m having a problem with my hp compaq cq41-208au
i was using win7 and then i install ubuntu 10.10 via internet.
after installing ubuntu it asks me for update and i accept it buh after it also ask me smthng grub and didnt notice what it says and just click restart
after i got a screen which says 
error : no such device : bed4e5bc-7d2e-486e-a365-14e5de8d236c
grub rescue>

<Note: i have two partitions sda1 sda2 both are HPFS/NTFS
and my win7 is install in sda1 and ubuntu in sda2 and sda1 is boot*

help me out plz

---

### Post by wilee-nilee on 2011-01-06
I think you need to reload the MS bootloader,  Solution 1
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If not a wubi do this.
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Feel free to ask questions I think you have a basically easy fix here, just the right tools to do it with, and a confirmation of your setup so we can get you fixed. ;)

---

### Post by Immolatus on 2011-01-06
OP said the machine has Win7 on. proly no backup media. They stopped doing that lately.

Boot the machine and interrupt from the splash screen then reinstall win7 from recovery partition. You said one of the was called "hpfs" so it is still there.

Next time burn a copy of the Ububtu iso image to disk and if you foul it up you can just use that disk to fix problems.):P

---

### Post by wilee-nilee on 2011-01-06
> **Immolatus said:**
> OP said the machine has Win7 on. proly no backup media. They stopped doing that lately.

Boot the machine and interrupt from the splash screen then reinstall win7 from recovery partition. You said one of the was called "hpfs" so it is still there.

Next time burn a copy of the Ububtu iso image to disk and if you foul it up you can just use that disk to fix problems.):P

Bad advice my friend a recovery disc is available and one command needed to reload the MS bootloader.

Read the link I posted this is a common problem and easily fixable.

I do agree with having a backup though.

---

