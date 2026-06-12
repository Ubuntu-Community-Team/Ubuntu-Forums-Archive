---
title: "Volume of drive on which Ubuntu installed"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by kewl_123 on 2009-07-11
Hi,
     I have XP and Ubuntu. Ubuntu is on one drive which is at least 40 GB.
However when I check the "Filesystem properties", it says Contents 9.8 GB and free space 970 MB. How is this possible?

---

### Post by Elfy on 2009-07-11
I would check trash first also have a look through this [http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

First - run ```
df -h
``` it will tell you the state of the drives you have.

---

### Post by prshah on 2009-07-11
> **kewl_123 said:**
> Hi,
     I have XP and Ubuntu. Ubuntu is on one drive which is at least 40 GB.
However when I check the "Filesystem properties", it says Contents 9.8 GB and free space 970 MB. How is this possible?

Ubuntu may be on a 10GB partition only. Is this a dualboot install or a wubi (via Windows) install? If it's a wubi install, you may have selected a size of only 10GB for the ubuntu file.

From within Ubuntu, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo fdisk -l
``` for an understanding of how the space is allocated on your 40GB drive. Post back the output here if you need an explanation.

---

### Post by kewl_123 on 2009-07-18
> **prshah said:**
> Is this a dualboot install or a wubi (via Windows) install? If it's a wubi install, you may have selected a size of only 10GB for the ubuntu file.

Its a wubi install ( Ubuntu appears as one of the programmes in add/remove programmes in XP), but I dont remember if I selected on 10 GB.

Heres the output of  sudo -fdisk l


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70707070

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       11473    51199155    7  HPFS/NTFS
/dev/sda3           11474       19457    64131480    7  HPFS/NTFS



There is a 493 MB file in trash which I am unable to delete.

---

### Post by Elfy on 2009-07-18
Run nautilus as root

```
gksudo nautilus
```

Navigate to your users trash - you will be able to delete it.

---

### Post by Paqman on 2009-07-18
> **kewl_123 said:**
> Its a wubi install ( Ubuntu appears as one of the programmes in add/remove programmes in XP), but I dont remember if I selected on 10 GB.


I'd say that's probably what you did. You should install LVPM and use it to [expand your Wubi virtual partition]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?").

---

### Post by kewl_123 on 2009-07-18
I referred to above article:

[B]"How do I create a virtual disk in Ubuntu?

Open a terminal (Applications -> Accessories -> Teminal), and enter these commands (this will create a 10 GB extra.virtual.disk, adjust line 2 to change these):

cd /host/ubuntu/disks
sudo dd if=/dev/zero of=extra.disk bs=1MB count=1 seek=10000
sudo mkfs.ext3 -F extra.disk"
[/B]


I gave the 3 commands and tried to create virtual disk. I dont see any addition of any disc in  Places --> Computer.
How do I know if I really got 10 GB extra and how do I use it?
I have 160 GB hard disc in all
Thank you.

---

### Post by Paqman on 2009-07-19
> **kewl_123 said:**
> I referred to above article:

[B]"How do I create a virtual disk in Ubuntu?

Open a terminal (Applications -> Accessories -> Teminal), and enter these commands (this will create a 10 GB extra.virtual.disk, adjust line 2 to change these):

cd /host/ubuntu/disks
sudo dd if=/dev/zero of=extra.disk bs=1MB count=1 seek=10000
sudo mkfs.ext3 -F extra.disk"
[/B]


I gave the 3 commands and tried to create virtual disk. I dont see any addition of any disc in  Places --> Computer.
How do I know if I really got 10 GB extra and how do I use it?
I have 160 GB hard disc in all
Thank you.

You already had a virtual disk. When you install using Wubi it installs Ubuntu onto a virtual disk located on your Windows partition. Your problem is that the virtual disk is now full. You want to consult the section regarding expanding your virtual disk. The easiest way to do that is to install LVPM like it suggests (LVPM = Loop-mounted Virtual Partition Manager, which is the techy name for your Wubi partition)

---

### Post by kewl_123 on 2009-07-20
I installed LVPM, transferred ubuntu to seperate drive and uninstalled ubuntu from add/remove programmes in windows. Now how do I know how much space I have for windows and how much for ubuntu?

sudo -fdisk l gives following message:

sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...


Also when I start my laptop, I get too many choices. How can I make it to two simple choices of Ubuntu and XP?

---

### Post by jeppewinther on 2009-07-20
Too many choices? If by that you mean you can choose between a number of known sane Linux kernels and Windows XP, I'd suggest you leave em be in case you mess something up and need to get back and fix something. Having an install you know you can fall back on is always a good thing.

If you want you can reorder them. The list is located at the bottom of /boot/grub/menu.lst

Run
```
gksudo gedit /boot/grub/menu.lst
```



You messed up that fdisk command slightly, the syntax is sudo <command> <operators>. That is
```
sudo fdisk -l
```
The Linux partitions should explain themselves, the line with NTFS in it is the Windows install.

---

### Post by kewl_123 on 2009-07-20
Thanks for pointing out the mistake in fdisk command.

And I will let the multiple options as they are.

In it, by default, the first option:

Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic

is chosen. I boot into that one. The other ones are

24-24-generic (recovery mode)
24-16-generic 
24-16-generic (recovery mode)
Ubuntu 8.04.3 LTS, memtest86+

So an I choosing the right option? It works, but still am curious.

Thank you.

---

