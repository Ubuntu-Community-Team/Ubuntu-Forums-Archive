---
title: "What is best way to add Vista and dual boot to a box with Ubuntu only already loaded?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by swarup on 2009-06-03
The HP laptop came with free DOS only. I installed Ubuntu on it. But now I want to create a dual boot with Vista/Ubuntu. I was going to remove Ubuntu, then load Vista, then shrink the Vista partition and install Ubuntu to the free space. Is there a better/faster/easier way?

And if you think my way is the best, then should I simply use my PartedMagic livecd to delete the Ubuntu and Swap partitions, and create an NTFS partition? Will that get me back to the original free DOS state, so I can install Vista? or am I going to end up with remnants of the GRUB boot loader which give me errors on startup? --If so, how to avoid this?

---

### Post by graphius on 2009-06-03
Windows doesn't like to play nice with others, especially its boot manager. Grub, which Ubuntu and many linux distros use recognizes windows, but the windows boot manager forces you to use only windows.
basically you have two ways to get the two operating systems on one machine. 
[LIST=1]
[*]Install windows first as you suggest
[*]install windows in a virtual machine
[/LIST]
I used to have xp on its own partion and dual boot. If you think you will use windows a lot, this is probably the way to go. It is a bit of a pain if you have your Ubuntu tweaked the way you like it. Do a full backup first, then restore.
Now I use [VirtualBox]("https://help.ubuntu.com/community/VirtualBox") for the occasional time I need to get windows (like translating stupid MS Publisher files for a client...) I don't need to reboot. With the included tools installed, I can cut and paste between windows and Ubuntu (That is SO handy). You do lose a bit of performance in windows, so I would not recommend it for gaming, but for me it works great.

---

### Post by prvteprts on 2009-06-03
FreeDos haha. My laptop had that preinstalled when I got it. Anyway, probably the easiest and most hassle-free way would be in my opinion:

1. Delete all existing partitions (start from scratch)
2. Create an NTFS partition - the size would depend on you, as long as it's not the entire disk obviously
3. Install Vista (why do you need FreeDos to do this?)
4. Run the Ubuntu Live CD, select manual install
5. Create an ext4 partition for Ubuntu with the remaining unallocated space (leave some space for swap)
6. Create a swap partition (1.5-2x the size of your RAM)
7. Install Ubuntu (GRUB will detect the Vista partition)

There is a method of installing Vista after Ubuntu that I know of, however it gave me a headache because it depended on this program which enables Vista to read ext filesystems, but it didn't work. It was so you could edit and re-enable grub or something. Anyway, the method above is my suggestion.

---

### Post by swarup on 2009-06-03
@ graphius: I see, yes-- very interesting. I may just try the virtual machine. But the Jaunty as currently installed has no sound. If I install Vista using the virtual box, will it use the Vista drivers and thereby provide sound? Or, since it is a virtual box, will it depend on the Jaunty drivers for sound and therefore be silent as well, until I get the Jaunty sound fixed?

@ prvteprts: Great information-- thanks. Now, just to confirm, once I delete the Ubuntu and Swap partitions, and before I install anything else, if I turn the computer on will it do the HP post and then come to a DOSS screen, as it originally did? Or would it give some GRUB error because the stage 1 GRUB boot loader is still present somewhere?

---

### Post by prvteprts on 2009-06-03
Good question. I am not sure... I think that would depend on if the FreeDos partition is still intact. Believe it or not, it actually has around a 50mb partition which I discovered after I installed Ubuntu. But, as far as I know, if you delete the Ubuntu partition, grub shouldn't show up anymore.

Anyway, does the grub error affect the installation in any way? If you pop in either the Vista DVD or the Ubuntu CD/DVD, it bypasses any bootloader, and after you install Vista or Ubuntu, the MBR gets rewritten anyway.

---

### Post by egalvan on 2009-06-03
> **swarup said:**
> I want to create a dual boot with Vista/Ubuntu. 
I was going to:
remove Ubuntu,
load Vista,
shrink Vista partition
install Ubuntu to the free space.
Is there a better/faster/easier way?

May not be the fastest, and only you can decide if it's the easiest,
but this procedure will give you the cleanest installs of both Vista and Ubuntu.

Virtual Vista will also be an advantage.

> 
should I simply use my **PartedMagic livecd** to delete the Ubuntu and Swap partitions, and create an NTFS partition?

I love, use** and support ($)** PartedMagic LiveCD, so thumbs up on this one.

> Will that get me back to the original free DOS state?
am I going to end up with remnants of the GRUB boot loader which give me errors on startup?
 --If so, how to avoid this?

Simply removing the Ubuntu partitions will leave GRUB, and the subsequent errors.

So yes, the first way is cleaner.

Windows likes being the only OS on a system,
and Windows likes being installed on the first primary partition.

GRUB and Linux play well with others, and don't Linux doesn't mind installing onto an extended partition.

---

### Post by egalvan on 2009-06-03
> **prvteprts said:**
> ...But, as far as I know, **if you delete the Ubuntu partition, grub shouldn't show up anymore.**

This depends entirely on WHERE GRUB is installed.
A default install puts GRUB on the MBR of the first hard drive,
where it will not be affected by any partitioning work.

> 
, does the grub error affect the installation in any way?
 If you pop in either the Vista DVD or the Ubuntu CD/DVD, it bypasses any bootloader,
 and after you install Vista or Ubuntu, the MBR gets rewritten anyway.

Absolutely.

---

### Post by graphius on 2009-06-03
A virtual machine will not be able to see devices which the host can't see.
I do know that sound is a bit touchy in Linux.
see the guide [here]("https://help.ubuntu.com/community/SoundTroubleshooting").
I also notice that once an a while, an update will set alsamixer to minimum sound, I have to go in through the CLI and increase it. I don't know why, and it doesn't happen often enough to trace it down.

I guess it comes down to why do you want to keep Vista? For me, as I said I only use it rarely, or to test websites, so a virtual machine is much easier.
For you it may be a better solution to dual boot, or even run Ubuntu in a virtual machine in Vista.

---

### Post by swarup on 2009-06-03
@ egalvan: Thanks for the great info!

> **egalvan said:**
> This depends entirely on WHERE GRUB is installed. A default install puts GRUB on the MBR of the first hard drive, where it will not be affected by any partitioning work.

So my question is-- and this is for my own education and future use, as it won't be mattering for this work for the reasons you and prvteprts have stated, but: If in the future, should I wish after installing both Vista and Ubuntu, to remove both and bring the computer back to its original Free DOS state, the way it was when I got it, then would simply using PartitionMagic to delete all the partitions I've created, do the trick? Or would grub still be remaining on the MBR of the first hard drive as you state above-- in which case how does one remove that to get back to the original state of the computer? Thanks!

---

### Post by swarup on 2009-06-03
@ graphius: Hey, thanks for the info.

@ egalvan/prvteprts: Well, I just did an experiment. I boot to PartedMagic, and in the partition editor went to Device->create partition table, and selected "create MSDOS partition table". It immediately deleted all data on the disc, so the entire disc was empty space (as I expected). But when I then rebooted, it first did the HP Post, and the after showing an intermediate screen something about looking for a link, arrived at a black screen with the message: "Disc error or non-system disc". It was not an MSDOS screen or command prompt as I expected to find. So why, after having selected to "create MSDOS partition table", am I getting this type of error on reboot? I was expecting it to be a very clean, MSDOS screen on reboot.

(anyway, as I said this is for my education-- as I am about to install Vista and then Ubuntu at this point anyway.)

---

### Post by graphius on 2009-06-03
by creating a partition table you are basically just setting up a table of contents for the drive. Now you need to put some content in.
Just like a book, you can make an outline of what you want to write about, but you still need to write the book. Your hard drive is now blank, it needs an operating system installed (now it has no operating system, and so is a "non-system disk"). So you need to make your choice now, do you want to reboot to get into the two operating systems? in that case install Vista. Then Ubuntu.
Are you going to use primarily Ubuntu, and rarely Vista, then install Ubuntu, then a virtual machine, then Vista.
If you are not sure at this point, I would install Vista first, as you can always delete it later (as I did with XP)

---

### Post by LewRockwell on 2009-06-03
> **prvteprts said:**
> Good question. I am not sure... I think that would depend on if the FreeDos partition is still intact. Believe it or not, it actually has around a 50mb partition which I discovered after I installed Ubuntu. But, as far as I know, if you delete the Ubuntu partition, grub shouldn't show up anymore.

Anyway, does the grub error affect the installation in any way? If you pop in either the Vista DVD or the Ubuntu CD/DVD, it bypasses any bootloader, and after you install Vista or Ubuntu, the MBR gets rewritten anyway.

also you should know that I have discovered that Ubuntu 9.04 will not necessarily show you all of a hard drive's partitions(but Puppy Linux always has)

---

### Post by egalvan on 2009-06-03
> **swarup said:**
> @ egalvan: Thanks for the great info!

So my question is-- this is for my own education and future use but: If in the future, should I wish to remove both and bring the computer back to its original Free DOS state, t
hen would simply using PartitionMagic to delete all the partitions I've created, do the trick? Or would grub still be remaining on the MBR of the first hard drive as you state above-- in which case how does one remove that to get back to the original state of the computer? Thanks!

Good mind set on the 'EDUCATION" angle...

No, merely erasing the partitions will not completely eliminate a default GRUB install.


GRUB installs part of itself in the Master Boot Record.
This can be restored by

fdisk /fixmbr

under DOS


check on herman's GRUB pages, lots of great info there.

hermanzone.


to COMPLETELY wipe a disk, try DBAN (Darik's Boot and Nuke)

dban.org

---

### Post by swarup on 2009-06-04
Hey thanks for the info. :p

And one last question: by telling PartedMagic to create the partition table, did that remove MS DOS (i.e. the the FreeDos partition)? Or is that still there. Because, I have never seen it there when I open gparted, even since the beginning.

---

### Post by rCXer on 2009-06-05
If a partition does not show up in gparted, it probably does not exist anymore.  If you really want FreeDOS, just recreate a small (mine is <1GB) Fat16 or Fat32 partition and install it using [its LiveCD](http://www.freedos.org/freedos/files/).  I think the disk includes a DOS port of gparted as well.  Alternatively you could install it on a virtual machine.

An easier way to use DOS is through an emulator such as [DOSBox](http://www.dosbox.com/).  You can find it the Synaptic Package Manager.

---

