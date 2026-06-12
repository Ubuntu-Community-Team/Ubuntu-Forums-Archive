---
title: "Cannot boot Ubuntu 10.04 LTS (32-bit) LiveCD"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Jabbadahut on 2010-09-30
Hello fellow Ubuntu users.  I have a problem with booting the LiveCD.

After I burned the CD, I booted the computer,& pressed F8 to get the boot menu to boot the CD drive.

When the LiveCD boot started, an error on my monitor appeared, stating "out of range."  Well, after fiddling around, I finally resolved that problem by pressing F6, and pressing F6 again in the menu that appears and selecting "nomodeset".

Then I chose the first option, to start the LiveCD without installing Ubuntu, but I get a different error upon booting up as follows:

```

(initranmfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/tput error

Cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.ashfs
```

Okay, sounds to me that something isn't right in the boot setup.

Here is the contents of the boot options file that appears on the menu.  Did I forget to add/omit something?

```

Boot Options file = /cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initid.lz quiet splash --|
```

I've used Ubuntu before, but this is my first attempt at running Ubuntu since I got a new system board & CPU back in Jan. 2009 (Asus M3N78 Pro).

If anyone can help me resolve this problem I'd be grateful.


- Jabba

---

### Post by Hippytaff on 2010-09-30
looks as though the stuff was either corrupted during burning the disc or the iso you downloaded is corrupt check the md5sum. - 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by andrewthomas on 2010-09-30
Is it an IDE or SATA drive?

I have an Asus M3A32-MVP motherboard and I have had to fool around with the BIOS settings to get some LiveCD's to work.

---

### Post by Jabbadahut on 2010-09-30
Checked the MD5 sum of the iso file I got, and it's okay.  Also, I have 2 dual layer DVD drives - both are IDE I believe (only one IDE slot on board, one installed as master & other slave.  Trying both gets me the same error.  If there is some setting in the BIOS that solves this, I have no clue what it is.  All I see as far as CDROM drives are concerned int it is the ability to change the their boot priority, & the IDE settings (what they are called I cannot recall now) which are all set to AUTO for both.  However, I am uncomfortable changing these as I don't want to cause any further trouble.

Upon further research, I found an old DVD disc where I had a copy of version 9.04 LTS 64-bit so I tried my luck with that.  Other than having to choose a "safe" graphics driver, Ubuntu actually boots the LiveCD.  So I am not really sure if changing the IDE settings for my DVD drives is the answer.

Since I got the older version to work, I think I'll stick with that for now & tackle version 10.04 at a later time. Thanks to you both for your help.

Now, how do I mark this thread as "[SOLVED]"?

EDIT - NM....Found it. :)

 - LL

---

