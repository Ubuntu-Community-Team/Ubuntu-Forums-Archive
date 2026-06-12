---
title: "Alternate CD installer help"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by sciberdude on 2011-02-04
The installer may be straightforward for more experienced users, but for me, the Alternate CD installer (Which was recommended in my previous thread) is confusing.

I got up to partitioning and my free space (80 GB) Is being used by Apple. (I'm on a Powerbook G4, 15", Ubuntu 10.10 Alternate CD) I tried resizing it, but the screen went red and told me I couldn't.

Is there any way to try it like in the Desktop version, or do I have to install it? And if I do, how do I partition half the disk?

---

### Post by NightwishFan on 2011-02-04
The alternate installer does not include the demo, it is only an install media. Also, the process is actually quite similar to the normal install even though it is keyboard based. As for partitioning, that is likely the only difficult step. It is much easier to "pre-partition" a system with a tool supported by your current OS, and leave free space open for ubuntu to automatically take advantage of.

---

### Post by lisati on 2011-02-04
> **sciberdude said:**
> The installer may be straightforward for more experienced users, but for me, the Alternate CD installer (Which was recommended in my previous thread) is confusing for me.

I got up to partitioning and my free space (80 GB) Is being used by Apple. (I'm on a Powerbook G4, 15", Ubuntu 10.10 Alternate CD) I tried resizing it, but the screen went red and told me I couldn't.

Is there any way to try it like in the Desktop version, or do I have to install it? And if I do, how do I partition half the disk?
I'm not familiar with the disk management tools available on Apple machines, but with some more recent versions of Windows it's possible (and sometimes better) to resize partitions within Windows before booting from the Ubuntu installation CD. Is this kind of option available for you?

---

### Post by jonnny_j22 on 2011-02-05
hi there. One of my linux machines is G4.

if you want to try the live cd again from usb this thread shows ho to get it on there

[http://forums.macrumors.com/showthread.php?t=598291](http://forums.macrumors.com/showthread.php?t=598291)
 
once you've got you're usb ready to go, unfortunately there's no sure certainty that your mac will automattically boot from the usb stick (I've found this hit and miss).
 
If you turn it on and it just ignores your stick, go into open firmware by pressing  the command, option, o and f keys all at once as you turn on the machine. 
 
from openfirmware use the command

boot usb1/disk@1:1,\\yaboot
 
you may have to try different number such as 0:1 or 1:2 depending on which usb your key is in and how the key is partitioned.
 
 
point 2 I definatly recommend using disk utility in osx to prepare your disk. Its not a great partition editor, but you can use it to free up the space safely - note you may have to do this from the osx install cd, i can't quite remember if disk utility lets you repartition once osx has booted. Basically free up the space you want for ubuntu as free space - maybe format it as fat and erase, just to be sure that it will stand out from any hfs+ partitions being used by mac.


Once you decide to install onto the free space, if you are using the live cd, it will be fairly easy to set up as you can clearly see whats going on. If however you are using the alternate or mini cd i think you have to create the partitions with mac-fdisk, which can be a little confusing  as it lists everything there, and osx actually has several small partitions and bits of free space between them scattered about which will all show up. make sure all the  partitions you create for ubuntu are in the free space you have allocated  previously and make a note of what you intend to mount on each one.
 
There is also a slight difference with linux on new world macs - you have to use mac-fdisk to create a bootstrap partition replacing the mac one so that it is the first partition in the partition table. This is where yaboot will go (the powerpc bootloader) if it isn't fist, it gets skipped by openfirmware and osx starts.
 
after this should be all the apple stuff and then your free space (apple likes to be at the start of the drive like windows) into your free space create a swap partition (twice the size of your ram) and then one or more ext3 orext4 partitions that you will use in the next step to mount the root, home and/or other directories as you want. 
 
Little tip - you can set the main hfs+ partition as your /home by setting the mountpoint there, so both mac and ubuntu share the same files - pictures and alike.
 
Any further questions please just ask

---

### Post by sciberdude on 2011-02-05
Alright, I partitioned a section using Disk Utility, and now I have a 20 GB section I'll use for Ubuntu.

What I'm really asking is what to choose when the partition is selected. Like, do I change "do not use". Or do I select the tiny free space below it? The partition says HFS+ like the normal one does, but without the Apple before it. I want to (for now) separate Mac and Ubuntu.

---

### Post by jonnny_j22 on 2011-02-05
you probably want to edit the partition before using it - delete it then in the free space that is created, make a partion formated as swap and then format the reast as ext3 or ext4. then select the swap and choose use as swap, and the ext partion use and mount point /

---

### Post by sciberdude on 2011-02-05
You are talking about from the installer, right?

I deleted my partition, leaving empty space. Should I go into the installer and format a new one (with the free space) as a swap? I don't have the installer open, so I can't really look at it to see what exactly you're talking about.

---

