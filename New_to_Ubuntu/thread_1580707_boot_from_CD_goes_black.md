---
title: "boot from CD goes black"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by chhillout on 2010-09-23
I've been trying for a few weeks now to install Ubuntu onto an old PC. I burned the CD properly (as far as I can tell). With the CD in the drive, I restart and all seems to be well (I see the white Ubuntu spots at the bottom of the screen and "Ubuntu" with the 5 dots ticking along) until immediately after, all goes black and just stays there. I've also tried booting from USB and it tells me "operating system missing". 

Except for the few weeks I've been trying to make this work, I'm a total n00b. 

The system is an old IBM R51 with <1 gb ram.

I'm aware Ubuntu supposedly needs 1 gb ram, will it run on less? 

I very much want to integrate Ubuntu/linux into my life and would appreciate the help. I've done a lot of wading through the forum and I've had limited success. 

Thanks in advance, kids and kittens! :KS

---

### Post by Jazzy_Jeff on 2010-09-23
Are you using the Live CD? If so try downloading the alternate install CD and use that. It is a text based installer but easy to follow. [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download). This link will get you to the download page.

---

### Post by papibe on 2010-09-23
It sounds like the installer is not able to initiate the graphic mode. You could try the alternative installer CD available at ubuntu.com. That one uses a text mode installer that works in most monitors/graphic cards.

There are more chances that the graphic mode works under the complete OS rather than just the installer.

Good Luck.

---

### Post by Chad Olson on 2010-09-23
Some older computers won't boot from usb you could try to update the bios so you can
  boot from usb.

---

### Post by chhillout on 2010-09-24
I used the alternate install CD and it went through the entire process smoothly. It told me the install had finished and ejected my CD to restart to the boot menu where it displays Ubuntu, Ubuntu Safe mode, two memory test options and xp. 

Choosing Ubuntu, it begins to load and then this message appears:

"Disk drive for /dev/mapper/cryptswap1 is not ready or not present." and below that:

Continue to wait; or press S to skip mounting or M for manual recovery

Then everything goes black again, same as how this started.

---

### Post by sikander3786 on 2010-09-24
See post # 11 in the following thread.

[http://ubuntuforums.org/showthread.php?t=1365261&page=2](http://ubuntuforums.org/showthread.php?t=1365261&page=2)

---

### Post by chhillout on 2010-09-25
I appreciate everyone's help with this. 

Sikander, referencing the other thread:

So for me two things were necessary:
1. keep the swap partition unencrypted by modifying fstab and crypttab
2. actually format the swap partion as a swap partition

1 - How do I modify fstab and crypttab, and modify to what? Is that done in GRUB? Or in the Partitioner during set-up?

2 - And how practically do I format the swap partition as a swap partition? 

I must confess I have not the faintest idea of how to approach doing that. Seems like it should be easy, but I'm almost totally ignorant of how these systems operate and how to manipulate them.

---

### Post by chhillout on 2010-09-25
I might be making headway..

I'm in the partitioner, editing the settings of my partition:

Partition settings:
 
  Use as: Ext4 journaling file system

Should I use the partition as a Swap area?

And for my mount point should I leave it set to mount from the root file system ("/")?

Leave Mount options set as default?

---

### Post by sikander3786 on 2010-09-25
I don't know much about your partitioning setup. I have never installed from the alternate cd either so I have no idea about that.

Anyhow, whichever disc you are using, format the partition as Swap area and its mount point is Swap not "/". "/" is used for root file system only. Swap needs to be on a separate partition.

---

### Post by papibe on 2010-09-25
These youtube videos may help:

[INDENT][Partitioning & Installing Ubuntu Server Part 1/2]("http://www.youtube.com/watch?v=bVjzt_uriwE")
[Partitioning & Installing Ubuntu Server Part 2/2]("http://www.youtube.com/watch?v=VAZRomlY8CE&feature=related") [/INDENT]

Good Luck!

---

### Post by chhillout on 2010-09-27
papibe, i followed that video and ended up with the same result. 

cryptswap missing..

i'm going to take a break from this junk for a few days and come back to it.

i appreciate everyone's help!

---

