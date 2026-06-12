---
title: "partitions"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by calreese on 2010-10-18
hey guys, i'm installing my first linux OS and i need help in the partitioning stage. size is not a concern as far as partition sizes go, and i have 4gigs of RAM. suggestions on swap, /boot, and /home sizes? thanks!

---

### Post by papibe on 2010-10-18
Check this tutorial: [Ubuntu Partitioning]("http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning")

I would recommend you:
[INDENT]/  10Gb
swap at least 4Gb
/home all the rest.[/INDENT]

Good Luck!

---

### Post by oldfred on 2010-10-18
Welcome to the forums.

Essentially agree with papibe. You should not have a separate /boot unless you have a very old computer with BIOS limits or are planning a server with RAID or LVM.

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

You will want 4GB swap if you want to hibernate otherwise 2GB will be enough as with 4GB of RAM swap should not normally be used.

If you are dual booting with windows you may want another partition for NTFS to share data with windows.

---

### Post by migs73 on 2010-10-18
If size is not an issue, and you plan to update every 6 month release, try havin two 10GB /'s. That way yo can put the new release on the extra / partition to play with till you have it all set up. That is what I have done with LL and MM and it has been very useful for setting up things like printer drivers, as I can copy from one to the other.

---

### Post by blueabysm on 2010-10-18
If you have 4G RAM, I think you don't need a swap partition.

---

### Post by coffeecat on 2010-10-18
> **blueabysm said:**
> If you have 4G RAM, I think you don't need a swap partition.

If you want to use hibernate, you definitely do. And unless you're very short on HD space it's still good practice. It's an extra margin of safety if you encounter an app with a bad memory leak.

---

### Post by Legeril on 2010-10-18
Agree with coffeecat, a little bit of SWAP is always good practice. SWAP is essentially some extra space your RAM can use if bogged down with an app or task running riot with memory

---

### Post by Hippytaff on 2010-10-18
Sorry to jump in and steal a question, but why is a /boot partition not recommended?

---

### Post by srs5694 on 2010-10-18
Some comments:


[list]
[*]I generally recommend 5-20 GB for root (/), depending on how much disk space is available and how much software you intend to install. A basic Ubuntu install consumes well under 5 GB, but if you start loading up software (adding KDE, development tools, locally-compiled kernels, etc.), you can get up to 10, 15, or even 20 GB, although reaching 20 GB will be a challenge.
[*]I agree with migs73 that a second partition for root (/) is worthwhile if you have the space to spare. That will enable you to test an upgrade before committing to it. You could also use it for another small installation to use in case of emergencies.
[*]I agree with coffeecat and Legeril on swap; given today's disk sizes, 4-8 GB of swap is cheap.
[*]I wouldn't go so far as to recommend *against* a separate /boot partition, but it's not really required on modern hardware. There are a few cases where it's useful or necessary, such as RAID or LVM configurations (particularly with GRUB Legacy), as oldfred mentioned. There are also a few filesystems that neither GRUB Legacy nor GRUB 2 can read (IIRC, Btrfs is one of them), so if you use such a filesystem for root (/), you'd need a separate /boot partition. One further advantage of having a separate /boot partition is that you can leave it unmounted most of the time. This has security benefits, since you're less likely to accidentally damage your kernel if the partition on which it's stored is unmounted. OTOH, I'm not sure if Ubuntu's various scripts relating to kernel upgrades and GRUB maintenance are smart enough to mount /boot, so you might need to do so manually if you leave /boot unmounted.
[/list]

---

### Post by blueabysm on 2010-10-19
> **coffeecat said:**
> If you want to use hibernate, you definitely do. And unless you're very short on HD space it's still good practice. It's an extra margin of safety if you encounter an app with a bad memory leak.
Yeah, hibernate function needs a swap partition at least as large as the RAM size. You are right:)

---

### Post by amjjawad on 2010-10-19
> **calreese said:**
> hey guys, i'm installing my first linux OS and i  need help in the partitioning stage. size is not a concern as far as  partition sizes go, and i have 4gigs of RAM. suggestions on swap, /boot,  and /home sizes? thanks!

The most common scheme is 3 partitions (root, swap and home).

1) 
/ partition (root)
Filesystem = ext4
size = 10-20GB

2) 
SWAP partition
Filesystem = Linux Swap
size: swap = RAM unless you have less than 2GB of RAM so I'd recommend swap = 2 * RAM or 1.5 * RAM.

3)
/home partition
Filesystem = ext4
size= the remaining size of your HDD unless you're dual booting with Windows.
[URL="https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning"]
More info is here[/URL]

---

