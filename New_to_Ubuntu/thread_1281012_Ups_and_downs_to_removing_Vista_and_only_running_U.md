---
title: "Ups and downs to removing Vista and only running Ubuntu?"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by halo45121 on 2009-10-02
Okay, I'm pretty much out of extra disk space. I have like 17mbs left.
Would Ubuntu operate any faster if I took Vista off? I don't have any attachments to Vista. Anything I need is on Ubuntu as well, and I don't have any important data on Vista. (well, all of it is backed up on jump drives and whatnot) Plus I can always just reinstall it, if something messes up with Ubuntu.
Okay, so if I were to remove Vista, how would this affect Ubuntu, and how would I go about doing this from Ubuntu?
Thanks!

Matt

---

### Post by fela on 2009-10-02
If you don't want vista then yeah, delete it I guess! There would almost certainly not be any performance hits though from having the vista partition.

To delete vista from Ubuntu you can probably just delete the partition with something like [gparted]("apt://gparted") (click to install, might work). You'll still have your entry in the grub menu for it but you can delete that by editing /boot/grub/menu.lst as root (gksudo gedit /boot/grub/menu.lst).

---

### Post by isee on 2009-10-02
Being in school, I have found that I need a Windows partition on my desktop, as some of the educational software is for Windows, and doesn't work well under Wine.  Also, I'm rather attached to my Canon photo management program, again for Windows.

My laptop is Linux only.  I rarely boot Windows on my desktop, but do occasionally.

Can you shrink your Windows partition to free up more for Linux?

---

### Post by DigitalAxis on 2009-10-02
Removing Windows would mean no more streaming Netflix, no ability to run programs that your workplace/university/institution requires (sometimes they do come up) that only run on Windows, and (unless you have had more luck than I) Microsoft Office... I can replace MOST of that with OpenOffice, but OpenOffice Impress is just not good enough to replace Powerpoint for me.  Replace that with Photoshop and the like as needed.  
There's also the possibility that Blu-Ray movie playback won't work for you without Windows and its DRM to prevent piracy, should a Blu-Ray disc ever implement it.  I'm going to assume that those really aren't your needs, though.

The only real reason I can see to keep Vista around in your case would be if you had the ext2fs driver for Windows installed; then Vista could become a way to rescue your Ubuntu partition and vice versa.  Although... Ubuntu liveCDs are free and plentiful.

On the other side of things, the presence of Vista on your system will, from Ubuntu's perspective, take up space.  The only way removing Vista will affect Ubuntu is if you were using the Vista bootloader to load GRUB to load Ubuntu. (rather than the more ordinary using GRUB to load the Vista bootloader to load Vista)

---

### Post by DigitalAxis on 2009-10-02
> **isee said:**
> Can you shrink your Windows partition to free up more for Linux?

Vista has a built-in disk partition utility that can shrink partitions, in case you weren't aware.  It's in Control Panel -> System Management (I think), somewhere down near the bottom.  If you can't shrink Vista enough, you can try defragmenting (or download something like Perfectdisk 10, and use 'Space Consolidation' and the 'system files' option, which will require a reboot)

---

### Post by Bartender on 2009-10-02
How much space you got, and what's on it?  Can you post the output of 
```
fdisk-l
```
or post a screenshot?  It would help to know what you're working with.

---

### Post by kansasnoob on 2009-10-02
Thinking only structurally, you could also run into boot problems if you remove Win!

I recently turned my 80GB drive into a testing drive after copying everything to a new 160GB drive using dd from a live CD.

Anyway, the problems begin if ALL of your Linux partitions are contained in an extended partition!

I'm not going to write a two hour tutorial but look here:

[ATTACH]130536[/ATTACH]

You can see that I've created another primary partition (in this case Karmic) so I can get rid of Win XP.

---

### Post by isee on 2009-10-03
I've never used Vista, I don't have it.  G-Parted is the main Linux partitioner, I believe.

---

### Post by theozzlives on 2009-10-03
As long as / is a primary partition you're ok. Just set it's boot flag, setup GRUB and it should be fine. If / is logical, you got problems.

---

### Post by oldfred on 2009-10-03
If you delete a partition you may have issues. If your Grub uses UUID it will be ok, but if it is root (hdx,y) the x & y will change. The same for fstab, if the entries are UUID no problem, but if sda2, for example, then it has to change to sda1.

---

### Post by Mark Phelps on 2009-10-03
You got lots of comments (any post against Vista DOES here), but to answer your questions more directly ...

> **halo45121 said:**
> Would Ubuntu operate any faster if I took Vista off? 

Since, I'm presuming you did NOT install Ubuntu inside Windows (using wubi), that basic answer is -- no.  The two OSs run each in their own partitions and neither one is sharing resources with the other at runtime.  So, there's no reason to suspect that Ubuntu will run any faster regardless of what other partitions are on the drive.

> ... and how would I go about doing this from Ubuntu?
Start GParted (you'll have to install it from Synaptic if it's not already installed).

Once GParted is open, select the MS Windows OS partition and delete it.

MS Windows is now gone.

Depending on how you installed GRUB, you may have to reinstall it from the LiveCD in order to be able to boot into Ubuntu again.

---

