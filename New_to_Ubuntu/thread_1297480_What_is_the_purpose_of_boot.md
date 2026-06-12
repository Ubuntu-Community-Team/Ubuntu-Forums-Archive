---
title: "What is the purpose of /boot?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by mispelt on 2009-10-21
Hi,

I've been using Linux for almost two years now (time flies, huh?) but until now I've never really felt like getting into specialty installations or anything like that. When I installed Mint, I thought ahead enough to partition /home separately, and it's been a blessing. I've borked my installation while playing around more than once, and... well, you know how it goes.

Anyway, I've been thinking about re-installing everything with a separate partition for /boot. I think I remember hearing you can store different kernels in there and select from them when you start things up. I was just wondering what the more seasoned among us have to say about the whole thing.

Thanks for your time.

---

### Post by pgar23 on 2009-10-21
[ HERE ]("http://www.linuxcommand.org/lts0040.php) is a very useful site that will explain some of the directories and a great place to get your beak wet in ubuntu. :) 
Hope that helps man.

---

### Post by pgar23 on 2009-10-21
But to answer your question...
/boot	This is where the Linux kernel and boot loader files are kept. The kernel is a file called vmlinuz.

---

### Post by whitethorn on 2009-10-21
> **pgar23 said:**
> [ HERE ]("http://www.linuxcommand.org/lts0040.php) is a very useful site that will explain some of the directories and a great place to get your beak wet in ubuntu. :) 
Hope that helps man.

The link doesn't work. :(

---

### Post by Pogeymanz on 2009-10-21
Keeping /boot on its own partition is not necessary any more. If I recall correctly, way back in the day there was a good reason, but I don't remember what it was.

Today, the only benefit would be that if you screwed up your / filesystem (power outage while writing data), you wouldn't hurt the boot stuff.

---

### Post by martrn on 2009-10-21
Having a separate /boot partition is good if you install more than operating system, or more than one distribution of one operating system because it allows you to put the kernels of your operating systems on a neutral filing system,  (can even by FAT16 etc), and then put all of your operating systems (or variants) on separate partitions each with its own separate file system. Brilliant if you are running OsX/Solaris/BSD/Linux/OS2/WINDOWZE/DOS/Other  and great for octal boot systems.

:confused:   :confused:

---

### Post by Bachstelze on 2009-10-21
It is also useful when your system lies somewhere you cannot boot from, like a LVM or RAID-0. In that cas, making a /boot partition outside the LVM/RAID is necessary to be able to boot your system.

---

### Post by Slim Odds on 2009-10-21
> **whitethorn said:**
> The link doesn't work. :(

That's because it looks like this: 
```
http://"http//www.linuxcommand.org/lts0040.php
```Try this instead: [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

---

### Post by Slim Odds on 2009-10-21
> **Bachstelze said:**
> It is also useful when your system lies somewhere you cannot boot from, like a LVM or RAID-0. In that cas, making a /boot partition outside the LVM/RAID is necessary to be able to boot your system.

Well said. I have RAID0 setup and a separate /boot partition for just that reason.

---

### Post by pgar23 on 2009-10-21
Go here, click "Learning the shell" scroll down to # 4. A Guided Tour.
It explain all the directories and functions of those directories.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

That was the link, sorry.

---

### Post by oldfred on 2009-10-22
A separate /boot also was when BIOS could only boot into the first part of the drive. You put the boot at the beginning.

Herman has a lot of info on /boot and on my preference /grub.
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

---

### Post by igknighted on 2009-10-22
You needed a separate /boot partition to use a / partition formatted as ext4 (with the old GRUB).  Also if you want to use some of the other file systems, such as XFS, you need a /boot that is something GRUB can read (eg, ext2).

---

### Post by Paqman on 2009-10-22
> **Bachstelze said:**
> It is also useful when your system lies somewhere you cannot boot from, like a LVM or RAID-0. In that cas, making a /boot partition outside the LVM/RAID is necessary to be able to boot your system.

You need an unencrypted /boot for full-disk encryption too, don't you?

> **igknighted said:**
> You needed a separate /boot partition to use a / partition formatted as ext4 (with the old GRUB).  

It would have to be a really old version of Grub. Jaunty will quite happily boot from an ext4 partition.

---

### Post by whitethorn on 2009-10-25
> **Bachstelze said:**
> It is also useful when your system lies somewhere you cannot boot from, like a LVM or RAID-0. In that cas, making a /boot partition outside the LVM/RAID is necessary to be able to boot your system.

Up until a week ago I had a raid 0 from two samsung drives, I was able to boot from it without having a seperate /boot.  I have an intel chip which set my raid in bios.

---

