---
title: "Partitions and boot booster"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by nauziem on 2010-04-02
I've recently purchased an Asus Eee 1005P and installed the Ubuntu 9.10 netbook remix on it just today.

I learned post-installation that by automatically installing it, I removed the partition which allowed for Boot Booster (a BIOS option that well... cuts down on boot time). What would be the easiest way (for a noob) to restore this? is reinstalling the OS a good/easy option, or is there a better route to change the partitions?

---

### Post by Crafty Kisses on 2010-04-05
I'm not sure how Boot Booster works, but I'm guessing it speeds up the boot time using cached data. In theory couldn't you just make a new partition and point Boot Booster to it? I'm not sure how Boot Booster works, but if there is an option in the BIOS to point out where it should look for the Boot Booster partition, then just make a new partition.

I guess I'm treating Boot Booster like a swap partition, but I'm not really sure how it works. Just putting my input in.

---

### Post by nauziem on 2010-04-05
Tyvm Crafty, I forgot I left this open actually... I worked it out this morning, it was as you said, the BIOS uses a small partition to cache information when booting and speeds it up. After some sluthing I worked out what I needed to do, which was

1. Copy gparted onto USB
2. Boot with it, shrink my major partition to create unallocated space
3. Reformat that to EFI with cfdisk (via terminal)
4. Reboot and enable Boot Booster from BIOS

---

