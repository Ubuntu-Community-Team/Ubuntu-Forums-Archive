---
title: "Ubuntu won't load"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by RageBoXx on 2010-07-26
I've got 2 physical hard drives. The first one has two partitions on it; Win7 on one and the other is empty. The second has three partitions; 3GB partition for pagefile (was this a stupid thing to do btw?), and two for music and documents. 

Now, I installed Ubuntu outside of Windows 7, on the empty partition on the first hard drive. Put the CD in, restarted the PC, booted from the CD, and chose to install. All went well. I chose a 50GB partition. It installed, no problem. 

Once I restarted my PC, I don't see the grub loader. I'm taken to Win7. I've checked that there's a 30 second timeout on the OS selection, and there is. 

What do I do? What am I doing wrong?

---

### Post by Rubi1200 on 2010-07-26
I am not saying you did this, but it does happen that people mistakenly install the bootloader on the wrong partition.
 
The best way for us to know what is going on is for you to boot the computer with a LiveCD and then click on the link at the bottom of my post.
 
Follow the instructions there and post the results back here.
 
Someone can then offer advice and solutions for your problem.
 
Good luck!

---

### Post by corncob on 2010-07-26
I'm thinking of last month when I was giving a presentation on Linux to the local computer club.  I had my laptop in front of me and the auxiliary VGA port connected to a projector with the screen behind me.  Although I had the time delay I wasn't seeing the boot menu which I wanted to demonstrate. I finally realized it was showing up on the projector screen but not on my laptop.  I'm just saying this in case you have two monitors with one turned off or facing away from you, although I would expect Ubuntu to be the default rather than Win7.

---

### Post by RageBoXx on 2010-07-27
I deleted the partition where Ubuntu was installed when I logged back onto Windows. So I'll install it again to get the results. 

Before I do that though, is there any particular location I'm supposed to put the boot loader during the install? I've got two partitions, a 50GB one for windows and boot, and an empty 200GB partition from which I took another 50GB during the Ubuntu install. So should I install the boot loader on the fist partition with Windows in it, or the second one?

Thanks!

---

### Post by aidenscool09 on 2010-07-27
Did it just skip Ubuntu and go straight to windows 7 or did it just give and error or just do nothing?

---

### Post by RageBoXx on 2010-07-27
It skipped and went straight to Windows. It didn't give me the grub loader. No errors though.

---

### Post by aidenscool09 on 2010-07-27
Try holding the Shift key while booting. It might go into GRUB.

EDIT:Oh yeah, you removed the partition didn't you.

---

### Post by corncob on 2010-07-27
> **RageBoXx said:**
> I deleted the partition where Ubuntu was installed when I logged back onto Windows. So I'll install it again to get the results. 

Before I do that though, is there any particular location I'm supposed to put the boot loader during the install? I've got two partitions, a 50GB one for windows and boot, and an empty 200GB partition from which I took another 50GB during the Ubuntu install. So should I install the boot loader on the fist partition with Windows in it, or the second one?

Thanks!

It sounds like you had installed the boot loader on the second partition with Ubuntu.  With win7 on the boot partition that's what comes up.  If you install the grub boot loader on the first partition it should work as expected.  However, if you remove Ubuntu again, windows won't work because grub's files are in the Ubuntu partition.  I'd install Ubuntu to the second HD and use BIOS to select it as the boot drive (assuming that it could do that).  Just some thoughts I'm throwing out -- somebody correct me if I'm wrong.

---

