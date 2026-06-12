---
title: "Dimension 4600 install problems"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Murflaw on 2009-05-14
Ok so my girlfriend gave me her old Dell Dimension 4600, and I was looking to use it as a spare pc to back up files on my server computer.  She warned me that it did not work, and I thought that I could fix it.  Well, I was wrong.  For the life of me I cannot get the Ubuntu live cd to work properly.  I have tried my ubuntu 8.04.1 cd and 8.04.2 cd, both of wich I know work since I used them to repair and reinstall ubuntu on my laptop many times over.  I even made new cd's, and still no luck.  I am able to access the live cd menu with no problem, but when I want to try ubuntu without changes to your computer either:
a.) the linux kernel loads and my screen and system freeze at xxx%, or
b.) the linux kernel loads, and I get the bar that bounces back and forth across the screen, for 10-20min, and it will give me thousands upon thousands of squash errors, or just stoop moving and not do anything.

As I am writing this I am running a system memory test so I will post outcome when it has finished.

---

### Post by pro003 on 2009-05-14
most likely you'll need an alternate version of install cd... you have images to download on main ubuntu site, just search for words - alternate i386 iso ... 

I had those problems, trust me I know.

---

### Post by utnubuuser on 2009-05-14
try one of the small distros like puppy or damn-small

I recently tried to put 8.04 and 8.10 on an older laptop without success, but 9.04 worked.
There's also #!Crashbang linux, which is made from the Ubuntu alternate CD - very nice.

---

### Post by Iusedtowearatie on 2009-05-14
The alternate CD theory sounds plausible. However, another theory:
I've experience this freeze phenomena with several distros, when trying to install later kernels on older machines. Turns out it has to do with power management functionality. In my case, booting with option acpi=off saved the day. This can be set right at startup, or permanently by editing the grub file (which of course requires a successful installation...).

---

### Post by pro003 on 2009-05-14
it seems like your girlfriend was right...

---

### Post by Murflaw on 2009-05-14
Hey guys thanks for the quick replies, the mem test was a no go was on all night and kept restarting itself, but always went to 100% w/o problems.

> **pro003 said:**
> most likely you'll need an alternate version of install cd... you have images to download on main ubuntu site, just search for words - alternate i386 iso ... 

I had those problems, trust me I know.

Ok I will try this asap...

> **Iusedtowearatie said:**
> The alternate CD theory sounds plausible. However, another theory:
I've experience this freeze phenomena with several distros, when trying to install later kernels on older machines. Turns out it has to do with power management functionality. In my case, booting with option acpi=off saved the day. This can be set right at startup, or permanently by editing the grub file (which of course requires a successful installation...).

I tried the acpi mode, will try it again but I don't think it will work.

I will try 9.04 also, but I believe that my problem is a bad cd drive, because even the windows xp cd gives me an error, but works on all of my other computers.

I am trying not to fork out any money on this computer, but if necessary I think I might have a spre cd drive lying around somewhere....

I will keep updates posted.

---

### Post by Murflaw on 2009-05-14
Also I don't know if it matters, but I have it plugged into my tv..

---

### Post by Iusedtowearatie on 2009-05-14
Can't see the TV connection has anything to do with it.
At this stage, considering your recent info, a HW issue with the CD drive seems more than likely.
If you have another computer available, you could use that to fire up the live CD and use that live system to prepare a Ubuntu USB stick. That stick can be used to boot the box with the possibly faulty CD drive, and you can also install to HDD from it.
This requires the box to have i BIOS that allows booting from USB flash disk which, sadly, is rare among older computers...

---

### Post by VoodooLoveDog on 2009-05-14
I installed 9.04 on that machine type not too long ago. I ran into issues with freezing, slow performance and remembered the issue with the Intel drivers that are in 9.04. I ran across this article that suggested to downgrade the Intel drivers back 2.4 from 8.10. That cleaned up my issues. 

Hope this helps.

---

### Post by Jazzy_Jeff on 2009-05-14
Here is another option for you. If you have a USB pen drive and your laptop will boot from a USB deice you can put Ubuntu on the drive. You can get a program called UNetbootin [here]("http://unetbootin.sourceforge.net/"). This is how I install all my distros.

---

### Post by Murflaw on 2009-05-15
I tried the alternate cd, and got past the loading linux kernel, and started to install but the cd told me my cd-rom was defective.  So, found that old cd-rom that was lying around(man. 1999), lol, and I was told I had no cd drive by the bios.  Then I realized I forgot to change the drive from slave to master, and vuoila it worked, installed ubuntu 8.04.2 no problem.

> **Jazzy_Jeff said:**
> Here is another option for you. If you have a USB pen drive and your laptop will boot from a USB deice you can put Ubuntu on the drive. You can get a program called UNetbootin [here]("http://unetbootin.sourceforge.net/"). This is how I install all my distros.

This USB pendrive boot, I did not try.  I will pick up a couple 2gb today and try this out, because the Dell bios says it supports it.  Whether the usb boot actually works is another issue.

Thank you everyone for the quick replies, and ideas.  I am off to find a cheap wireless card so I can update this badboy.

---

