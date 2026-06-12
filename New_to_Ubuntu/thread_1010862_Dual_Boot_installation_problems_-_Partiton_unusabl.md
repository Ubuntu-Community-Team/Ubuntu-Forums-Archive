---
title: "Dual Boot installation problems - Partiton unusable"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Nico-dk on 2008-12-14
Hi all.
As I type this, I'm in the middle of setting up a Dual Boot (XP / ubuntu 8.04).

This is a Dell XPS M1530 that came (today) preinstalled with Vista 32 bit.

I've been following a guide that takes the dreaded Media Button into account.

So far I've
1) Installed XP (with a slipstreamed CD)

2) Created the following logical partions with EASEUS partion manager:
30GB Games - NTFS
12GB Audio - NTFS
16GB Graphics - NTFS

3) Booted up ubuntu via CD, double clicked Install

4) At the prepare disk space I had the following listed:

/dev/sda1 - Fat16 (Dell utilities) - Primary
/dev/sda2 - NTFS (XP) - Primary
/dev/sda5 - NTFS (Games) - Logical
/dev/sda6 - NTFS (Audio) - Logical
/dev/sda7 - NTFS (Graphics) - Logical
Free space

5) I chosee the free space and specified:
Primary partion
Beginning
12gb
ext3
Mount: /

This is created, and /dev/sda4 / - ext3 is added to the list of partitons 8after a scan of course).

6) **THIS IS WHERE I'M STUMPED**
There is no free space left. Ubuntu can see the remianing space, but it's listed as unusable, so even if I highlight it, I can't choose to create a partition.

I'm a newbie, and I'm sure i did sopmething wrong, but I have no clue what?? Any and all help will be greatly appreciated.

I'm thinking this has to do with the multiple ntfs partitions, and my only solution right now is either starting from scratch or deleting my ntfs partions and merge them into my XP partition.
Then I'll just have to worry about what will happen when I create those partiton after Ubuntu has been installed.

Not that I think it matters, but these are my specs:
T8300 Core 2 Duo (2,40Ghz, 800Mhz)
4Gb DDR2 SDRam @ 667Mhz (2x2)
160Gb HDD
256mb Geforce Go 8600M GT

---

### Post by Nico-dk on 2008-12-14
AHA!
Putting Ubuntu at the end let's me create more partitions, then my questions is, should I create /boot or / first?

I plan to do a /home last so it sit snuggly in the middle.

---

### Post by bumanie on 2008-12-14
Any hard drive has the limit of having a maximum of 4 primary partitions. You will need to make another logical/extended partition to install ubuntu into. Primary + Primary + Logical (with three partitions) = 3 primary partitions. An extra primary as / makes the fourth primary partition. Looks as though you were doing everything right except for that detail.

---

### Post by Nico-dk on 2008-12-14
*edit*
Ooops, see you added some additiona info.

I might start over anyways, because it seems the dell utils partion is just a bootable image of a cd that also came with the comp

Strange that I can make a Primary at the end of the disk though

---

