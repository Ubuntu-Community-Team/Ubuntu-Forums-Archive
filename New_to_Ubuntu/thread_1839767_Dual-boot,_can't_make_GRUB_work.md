---
title: "Dual-boot, can't make GRUB work"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by zcacogp on 2011-09-06
Chaps, 

This thread follows on from an earlier thread, here: 

[http://ubuntuforums.org/showthread.php?t=1836040](http://ubuntuforums.org/showthread.php?t=1836040)

To summarise it, I changed the HDD in my computer and tried to swap the partitions over from the old one to the new one to avoid having to re-install everything (it's dual-boot, with XP and 11.04.) I managed to swap the partitions over fine, but couldn't make things boot as they should. I'd like to be able to boot into GRUB, which would then give me a choice of which operating system to load. (Which is exactly what happened - effortlessly - with the old HDD in place!) 

I repeatedly failed to make it boot properly, and eventually re-installed Ubuntu onto sda2, which caused the computer to boot through GRUB to Ubuntu. I then re-installed XP to sda1, which, in turn, caused the computer to boot straight into XP. This is what I expected. 

Next stage was to re-install GRUB so that it would pick up the newly-installed XP, and allow me the choice of OS's on booting. So, using this thread here: 

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

... I booted using a live CD (Natty, as I have a Natty install, so all  GRUB v.1.99) and used the following commands to re-build GRUB: 

```

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

It completed the command and reported no errors. However the computer now boots to a GRUB prompt ('grub>'), and I can't understand why. I can re-boot using the live CD and enter the commands above, and it still boots back to the GRUB prompt. I can re-boot using the XP installation CD, work through to the recovery console and enter "fixboot" and "fixmbr" and it still boots back to the GRUB prompt. 

So ... how do I get beyond this? 

(This is placed in Absolute Beginner as I am really struggling with this, and yet can't understand why it isn't working. I really am feeling like a complete beginner ... )

Thanks, in advance, for any help you can offer. 


Oli.

---

### Post by Bucky Ball on 2011-09-06
Try [THIS]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html")

It will reinstall grub to the MBR and all should be good. It will pick up all OSs and include them.

---

### Post by zcacogp on 2011-09-06
Bucky Ball, 


Many, many thanks! To my surprise that worked just fine, and the machine will now boot into both Windows and Ubnutu! 

Thanks again. 


Oli.

---

### Post by Bucky Ball on 2011-09-07
Love it when a plan works out! That is a great little app and thanks Yann for the hard work. ;)

---

### Post by zcacogp on 2011-09-07
It **is** a great little app - it saved my bacon.

Many thanks Yann. And thanks to you BuckyBall for pointing me in it's direction. 


Oli.

---

