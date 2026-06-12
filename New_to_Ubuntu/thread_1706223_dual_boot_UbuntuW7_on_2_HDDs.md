---
title: "dual boot Ubuntu/W7 on 2 HDDs"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by verymadpip on 2011-03-13
Hello all.
I've done a little searching & I think I know where I'm up to, but I'd appreciate some clarification on my plan.

I intend to install W7 on a second HDD (160Gb) which is IDE.  I already have Ubuntu 10.10 (64 bit) installed on a 750Gb SATA HDD.  I would like to be able to choose which HDD to boot on startup without having to enter the BIOS to do so.  I believe that GRUB 2 can handle this.

As I understand it I disconnect the SATA HDD (Ubuntu), install the IDE HDD as master & then install W7.

I understand that SATA has no master/slave designation, but the IDE HDD has to be set to something, right?  I'm going from what I've read so far when I say it'll be set to master.

I then either:

A.  Reconnect my SATA (Ubuntu) HDD & run update-grub

or:

B.  Do a fresh install of Ubuntu with the IDE (W7) HDD connected so that GRUB 2 will find said IDE (W7) HDD.
I expect I'd need to do an update-grub at this point too.

It seems to me that option B looks like the best one.

A fresh Ubuntu install is no problem as I'm on kind of an interim set up at the moment following a bit of a tech disaster last week.

This probably won't be happening for a couple of days as I'm waiting for  W7 to arrive.  Effectively W7 will just be a Call of Duty Box.

Am I on the right track?
Any help & suggestions would be greatly appreciated.

Thanks folks.

---

### Post by Mark Phelps on 2011-03-13
Have similar setup ... so, simply do the following:
1) Install W7 to the other drive -- with only that drive connected
2) Reconnect Ubuntu drive, reboot PC -- but go into BIOS to boot the Ubuntu drive first.  BIOs typically place the IDE drive "first" in the BIOS, ahead of SATA drives, but that is not always the case.
3) When in Ubuntu, run  "sudo update-grub".  That will regenerate the GRUB  menu for you.
4) Reboot and use the GRUB menu to choose.  Be advised that since you have Win7 on a separate drive, GRUB may provide two menu choices for it.

---

### Post by verymadpip on 2011-03-13
Hi Mark.

Aha, that's the bit I'd forgotten - changing the HDD boot priority in BIOS.

That's great thanks Mark.

I'll come back when it's done & hopefully be able to mark the thread solved.
That'll be a couple of days yet though.

Thanks again :D

---

### Post by YesWeCan on 2011-03-13
You are doing all the right things. Option A will be fine provided you installed Ubuntu's Grub MBR on Ubuntu's SATA drive and not on the IDE drive.

To make sure Grub is installed to the right drive you can boot Ubuntu and then run 'sudo fdisk -l' to see the letter designation of the Ubuntu drive. Then run 'sudo grub-install /dev/sdx' where x is the letter of the Ubuntu drive.

The update-grub command causes grub to scan all your drives to look for OSes. It will automatically add your Win7 to its bootloader.

BTW you also have the option to use Win7 bootloader to boot Ubuntu. This can be done using EasyBCD, a free download for Windows.

---

### Post by verymadpip on 2011-03-13
Thanks YesWeCan.  I think I'll stick with the plan so far :D

This has been something of an adventure for me anyway.  HDDs, different cables, drive bays, finding stuff on the mobo.  If I'm honest I never thought I'd see the day when I'd be doing any of this stuff, but you live & learn eh?

I have another question:

Why might I end up with 2 menu entries for W7?

Thanks muchly guys,

Pip

---

### Post by verymadpip on 2011-03-16
That's all gone swimmingly well guys.  I used option A.

Scary message about no such device on the first Ubuntu boot from the GRUB menu, which was promptly followed by a normal boot (as far as I can tell).

A little difficulty physically getting the second drive, in & a day & a half's frustration trying to install W7 until I told my PC it doesn't have a floppy drive, even though it thinks it does (what the..........?)

Thanks again folks.

Pip

---

### Post by uncommoner on 2011-10-16
"1) Install W7 to the other drive -- with only that drive connected
2) Reconnect Ubuntu drive, reboot PC -- but go into BIOS to boot the Ubuntu drive first.  BIOs typically place the IDE drive "first" in the BIOS, ahead of SATA drives, but that is not always the case.
3) When in Ubuntu, run  "sudo update-grub".  That will regenerate the GRUB  menu for you.
4) Reboot and use the GRUB menu to choose.  Be advised that since you have Win7 on a separate drive, GRUB may provide two menu choices for it."

Mark,

Thank you. I'm a new escapee from the "gates of hell," and while I love Ubuntu I am hooked to Win7 for pro audio purposes for the time being.

I don't want to have endless hardware, I have anything up to 10 computers running at any one time as it is. It's hard to keep up.

I tried the, "running Ubuntu and Win7 together on the same drive," but it just didn't work to my taste.

So, finding this solution, (I can fit 7 disks in both my main machines,) I'm well sorted.

Cool, very cool. Thank you.



brendan

---

### Post by ydoc on 2011-10-16
> **uncommoner said:**
> "1) Install W7 to the other drive -- with only that drive connected
2) Reconnect Ubuntu drive, reboot PC -- but go into BIOS to boot the Ubuntu drive first.  BIOs typically place the IDE drive "first" in the BIOS, ahead of SATA drives, but that is not always the case.
3) When in Ubuntu, run  "sudo update-grub".  That will regenerate the GRUB  menu for you.
4) Reboot and use the GRUB menu to choose.  Be advised that since you have Win7 on a separate drive, GRUB may provide two menu choices for it."

Mark,

Thank you. I'm a new escapee from the "gates of hell," and while I love Ubuntu I am hooked to Win7 for pro audio purposes for the time being.

I don't want to have endless hardware, I have anything up to 10 computers running at any one time as it is. It's hard to keep up.

I tried the, "running Ubuntu and Win7 together on the same drive," but it just didn't work to my taste.

So, finding this solution, (I can fit 7 disks in both my main machines,) I'm well sorted.

Cool, very cool. Thank you.



brendan

If you don't mind me asking, what hardware are you running?  I was running M-Audio hardware for a while, just a little MBox, and I had the WORST time finding any way to run it with Win 7 x64.  I ended up having to install Windows XP again just to take advantage of my hardware interface.  I'm glad to hear that pro audio hardware developers finally started producing hardware for Win 7.

---

