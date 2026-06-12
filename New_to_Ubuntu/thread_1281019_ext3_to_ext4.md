---
title: "ext3 to ext4?"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by samh785 on 2009-10-02
So, I've heard that that Karmic Koala is going to include ext4 as the default file system. Right now, I'm running Jaunty and I have ext3. I've heard that it will leave the existing file system in place unless I install the new release from scratch (which I do not want to do). How would I go about upgrading my file system without erasing all of the data on my drive?

Thanks in advance, 
Sam

---

### Post by NoaHall on 2009-10-02
You can upgrade it, but you won't get better performance. To get better performance, you should reinstall. There are a lot of problems if you don't. Although you can use ext3 in 9.10 too.

---

### Post by Cope57 on 2009-10-02
ext4 has been out since 2006, and went stable in 2008.  So, what is holding you up to upgrading?

64bit CPU's have been available since 2004, and people are still using 32 bit processors.  I have been using 64 bit since Nov 2004, and I am waiting for 128bit CPU's to come out.

---

### Post by JC Cheloven on 2009-10-02
> **samh785 said:**
> So, I've heard that that Karmic Koala is going to include ext4 as the default file system. Right now, I'm running Jaunty and I have ext3. I've heard that it will leave the existing file system in place unless I install the new release from scratch (which I do not want to do). How would I go about upgrading my file system without erasing all of the data on my drive?

Thanks in advance, 
Sam

I didn't try myself, but this should work:

1) Save your present ext3 filesystem to an external media, as an usb external disc. Use fsarchiver for that, which is included in [SystemRescueCD]("http://www.sysresccd.org/Main_Page").
2) Use gparted from live cd to format your ext3 partition to ext4 (you'll erase the data in the partition at this point, it cannot be avoided).
3) Use fsarchiver again to restore the filesystem that was in the ext3 partition, to the ext4 one (yes, fsarchiver can do that).
4) From live cd, change the UUID's in the files /etc/fstab and /boot/grub/menu.lst as apropriate. You can find the UUID of the newly created ext4 partition using "sudo blkid".
5) Upgrade the distribution to karmic

I hope not to miss anything. Not to say that it's immediate, but it's the only way I have in mind at this moment. If you do it, please let us know how was it.

---

### Post by samh785 on 2009-10-05
I just upgraded to 9.10 and got the full-on ext4 with all of the performance boosts :P

---

### Post by lavinog on 2009-10-05
> **Cope57 said:**
> ext4 has been out since 2006, and went stable in 2008.  So, what is holding you up to upgrading?

The kernel that originally came with jaunty had a bug where deleting a large file on ext4 file systems would crash the system...There was even a warning not to use ext4 in jaunty for production machines.

---

### Post by infestor on 2009-10-05
is ext4 really that great over ext3?

---

### Post by samh785 on 2009-10-05
> **infestor said:**
> is ext4 really that great over ext3?

not enough to warrant me reinstalling my whole system probably, but I'm sort of OCD about things like this. :P

---

### Post by slakkie on 2009-10-05
ext4 is going to be the new default. But I'm waiting for the next LTS to clean install. So in roughly 7 months time I will have ext4 as well.

---

### Post by running_rabbit07 on 2009-10-05
> **infestor said:**
> is ext4 really that great over ext3?

I noticed a bit of a difference when I changed over. I have switched back and forth a few times, as I destroyed installs doing other things, and EXT4 has been really stable for me.

---

### Post by running_rabbit07 on 2009-10-05
> **slakkie said:**
> ext4 is going to be the new default. But I'm waiting for the next LTS to clean install. So in roughly 7 months time I will have ext4 as well.

You are going to clean install?[-( 

Just playing. Yeah, it is worth it. So far Karmic is working reat in my VBox, so I will upgrade to Beta a few days before the full release.

---

### Post by slakkie on 2009-10-05
> **running_rabbit07 said:**
> You are going to clean install?[-( 

Just playing. Yeah, it is worth it. So far Karmic is working reat in my VBox, so I will upgrade to Beta a few days before the full release.

I know, unheard off :)

Actually, I think clonezilla needs to support ext4 before making the switch.

---

### Post by lavinog on 2009-10-05
Keep in mind, if you dual boot: There isn't any ext4 support for windows yet.

---

### Post by mikechant on 2009-10-06
> is ext4 really that great over ext3?

I noticed that it gave me a 30%+ improvement in boot time on my eeePC**, and I've seen benchmarks also showing large speed improvements.


**Comparing fresh installs of Jaunty Netbook Remix, both identical apart from ext3/ext4 use for /

---

### Post by mgranet on 2009-10-06
Fsck on ext4 is much faster. What used to take minutes now takes just a few seconds.

---

### Post by CharlesA on 2009-10-06
> **slakkie said:**
> I know, unheard off :)

Actually, I think clonezilla needs to support ext4 before making the switch.

Unless their site is wrong, clonezilla supports ext4.

> Filesystem supported: **ext2, ext3, ext4**, reiserfs, xfs, jfs of GNU/Linux, FAT, NTFS of MS Windows, and HFS+ of Mac OS. Therefore you can clone GNU/Linux, MS windows and Intel-based Mac OS, no matter it's 32-bit (x86) or 64-bit (x86-64) OS. For these file systems, only used blocks in partition are saved and restored. For unsupported file system, sector-to-sector copy is done by dd in Clonezilla.

I'll probably bump up to 9.10 when it's released and make my main drive and raid array ext4.

---

### Post by bubblehead74 on 2009-10-06
> **lavinog said:**
> Keep in mind, if you dual boot: There isn't any ext4 support for windows yet.

How do you mean?

---

### Post by CharlesA on 2009-10-06
> **bubblehead74 said:**
> How do you mean?

Guessing by using the fsdriver for windows. Could be wrong tho.

---

