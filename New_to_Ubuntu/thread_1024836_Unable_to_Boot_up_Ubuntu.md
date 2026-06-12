---
title: "Unable to Boot up Ubuntu"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by dorian246 on 2008-12-29
Hey guys, Thanks for your help the first time. I got Ubuntu installed and working great. I was loving it at first but however I've run into a snag...

As Usual I shut it down last night, This morning when I go to run it starts up as normal getting to the grub loading screen telling me to hit escape to access the menu. However right after it I get this. I copied it down word for word:


Boot from (hd 0. 0) ext 3 f2690069. 9401. 03e- 9dea 0 bfcc82b42458

Starting up...

[       0.166384] ACPI: Aborted because junk in compressed archive

[      1.215062] Invalid compressed format (err=2)

[   1.236954] kernal panic- not syncing VFS: unable to mount root fs on unkown block
(0. 0)





And it freezes there. I tried running it in saftey mode to avail either...Does anyone have ANY idea what could be going on here?

Thanks for any help in advance you can offer and a belated merry Christmas :).

---

### Post by mapes12 on 2008-12-29
Looks like your drive has had compression software on it at some point. Probably from a windoze installation. To solve the problem I would run a low level format utility across the drive then do a fresh install of Ubuntu. A freeware low level format utility can be found [here]("http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/").

---

### Post by dduehning on 2008-12-29
Before you format...

I had an issue very similar to this, and found that I had bad ram.  To verify/check it out in your case, boot from the ubuntu cd that you installed from and run memtest.  I know it's also part of the boot options in ubuntu, but that's based on default settings, etc.  Just a thought, and it's easy enough to check before formatting and losing any data/settings/etc.

---

### Post by caljohnsmith on 2008-12-29
In addition to following dduehning's excellent suggestion to check your RAM, I think it would also be good to do an "fsck" file system check on your Ubuntu partition to make sure there aren't any issues along those lines. If you can boot your Live CD, open a terminal (Applications > Accessories > Terminal) first do:
```
sudo fdisk -l
```
And from that output, determine which partition is Ubuntu, and then do:
```
sudo fsck -yCM /dev/[COLOR="Blue"]sdaX[/COLOR]
```
And replace "sdaX" with your Ubuntu partition. Let me know if that makes any difference.

---

### Post by dorian246 on 2008-12-29
Hey guys thanks for the responses.

Sorry im really new to this so im going to need clarfication on a couple things....

To Mapes how can I run that program? I can't unfortunately get onto my computer...and unfortunately when I try run it threw the live disk it just crashes.... I don't have a lot of ram on this computer I installed it on now so im thinking it might be a ram issue....


So two questions, How do I do a fresh install? Do I have to remove the old one first, or can I just insert the disk and just install it again? If I have to remove it how do I do that?

Also with the memtest...I've run it before but im not quite sure what it means or how to tell if I have bad ram (which I think is the problem....) how long do I leave it running for and does it tell me if ram is indeed the issue?

Thanks for the help...

---

### Post by mkvnmtr on 2008-12-29
You did not say do you only have Ubuntu installed on this computer?

---

### Post by dorian246 on 2008-12-29
> **mkvnmtr said:**
> You did not say do you only have Ubuntu installed on this computer?

Sorry yes only Ubuntu

---

### Post by dorian246 on 2008-12-29
So I ran the RAM test and that was not the problem :(...

I think I've figured out how to re-install it so im going to wipe it and re-install....hopefully that fixes it...should I still run that program though will that work on linux?

---

### Post by dduehning on 2008-12-30
Typically a low level format is not needed, even if compression was used on the drive.  In most cases just wiping out the partitions will take care of that.

---

