---
title: "Just a precaution"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-03-09
I just need a quick 'takealook'. I'm about to install Sabayon on another partition. Here is some output if needed. 


ivan@ivan-desktop:~$ sudo fdisk -l
[sudo] password for ivan: 

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x076c076c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5083    40829166    7  HPFS/NTFS
/dev/sda2            5084        9964    39206632+   f  W95 Ext'd (LBA)
/dev/sda5            5084        9964    39206601    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3012f93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       18124       18247      996030   82  Linux swap / Solaris
/dev/sdb2               2       18123   145564965    f  W95 Ext'd (LBA)
/dev/sdb3           18248       19457     9719325    7  HPFS/NTFS
/dev/sdb5               2        9670    77666211    7  HPFS/NTFS
/dev/sdb6            9671       14204    36419323+   7  HPFS/NTFS
/dev/sdb7           14205       18123    31479336   83  Linux

Partition table entries are not in disk order

The idea is a clean install on one of the partitions of /dev/sdb. Both /dev/sda and /dev/sdb have GRUBs on them and Ubuntu is loaded from /dev/sdb. Do I need to take any precaution with this multi-boot regarding boot-loader options etc?

---

### Post by hyper_ch on 2009-03-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by bodhi.zazen on 2009-03-09
> **ivanvajar said:**
> The idea is a clean install on one of the partitions of /dev/sdb. Both /dev/sda and /dev/sdb have GRUBs on them and Ubuntu is loaded from /dev/sdb. Do I need to take any precaution with this multi-boot regarding boot-loader options etc?

Well, it sounds like, rather then taking a little time to learn how to use grub, you are making them more complicated then they need to be. At least I am getting the impression you are asking for someone to look at what you are doing ?

My advices is to learn how to use grub, it is not that hard, takes 15-30 min.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

Otherwise you partitions seem "out of order" , not a big deal, but can be fixed with fdisk if you wish :twisted:

Otherwise what do you need advice on exactly ?

---

### Post by ivanvajar on 2009-03-09
There are two boot loaders 'cause I needed my second HDD (the one containing Ubuntu) to be bootable even when I move it to another computer. Ubuntu was installed on another computer (that had internet connection), similar to mine and that HDD was installed on my machine (that didn't have internet connection at the time) later. That's why there are two boot loaders installed. The question is: If Sabayon's boot loader is installed in MBR on sdb, will it recognize Ubuntu installation?

I'm wondering if adding Sabayon to the boot loader that is already there is a better idea then installing a new boot loader.

---

### Post by bodhi.zazen on 2009-03-09
Take a look at the second link I gave you. I have no idea if Sabayon will recognize Ubuntu, usually they do, but not always.

It is easy to configure grub, however, post install.

---

### Post by ivanvajar on 2009-03-09
I didn't tell that on sda is Windows boot loader and GRUB on sdb. Sorry :-)

---

### Post by ivanvajar on 2009-03-09
Thank you.

---

