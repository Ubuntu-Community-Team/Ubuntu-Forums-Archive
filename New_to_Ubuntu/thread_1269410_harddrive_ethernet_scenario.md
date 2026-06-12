---
title: "harddrive ethernet scenario"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by tchk1 on 2009-09-18
ok first of all i'm sry i'm totally retarded or something
i'm formatting a hard drive after install like this
i create an primary harddrive then a 5 gb swap at the beginning and end [not sure where outside of disk is but was told it's faster then interior] then ext4 in the middle of them tried primary and logical
then i restart and i can't write to them because i'm not the root but i just created them, gparted didn't let me specify partion permissions. i guess since gparted asked me password that makes me root is there a partition editor with some real options or do i just have it set up totally wrong or what?
also my mobo's ethernet ports just stopped working when i plug in cable no lights letting me know it's trying to communicate or anything, then if i plug in a nic card to pci slot and connect cable it automatically connects without even power cycling my modem. i never had problem with ultimate edition using these connections before i even loaded setup defaults in bios still no luck maybe i should try to reset cmos or something with the mobo jumpers [asus m2n-sli deluxe]
with two ethernet ports

---

### Post by HarrisonNapper on 2009-09-18
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by ayenack on 2009-09-18
Take a look at this. It's an in-depth tutorial on creating a mount point the right way.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I wouldn't reset your MOBO if I were you try to diagnose the problem first. Put a post in the Network & Wireless section of the forums.

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

