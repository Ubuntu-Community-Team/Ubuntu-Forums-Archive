---
title: "Grub problem..."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by LoveOutLoud on 2009-02-18
Hi, 

I usually lurk around these forums to try and find an answer to one of my problems, and I have always been successful..
until now :(

I've tried various fixes to it already, but no luck.

Here's the scenario. 
I have Ubuntu installed on my laptops HD. I have XP Pro on an external HD. I can load Ubuntu fine, with and without the external plugged in. When i try to select XP, It tells me there was an error reading the disk and to restart.

I went into the **menu.lst** and added:
```
title Windows XP Professional
root (hd1,0)
makeactive
chainloader +1

```

Here is the output I get when I do** fdisk -l**

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7352d69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29270   235111243+  83  Linux
/dev/sda2           29271       30401     9084757+   5  Extended
/dev/sda5           29271       30401     9084726   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
48 heads, 46 sectors/track, 442379 cylinders
Units = cylinders of 2208 * 512 = 1130496 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      442379   488384512    7  HPFS/NTFS

```


Any possible solutions? Help is very much appreciated =)

---

### Post by handy on 2009-02-18
It has been a few years that I have been away from the windows world.

But if my memory serves me well, you could have an awful lot of trouble trying to get XP or any other version of windows to boot if it didn't think it was on the C: drive.

---

### Post by ken_34 on 2009-02-18
You could try to boot from a windows XP installation cd and select the repair option instead of install. If it recognizes your external HD it will try to repair your XP startup

---

### Post by pablolie on 2009-02-18
it *looks* like it ought to be ok. strange. the same grub entry, with a slightly different configuration, works in my dual boot system.

is it an external USB drive? is your BIOS boot setup ok?

PS: i'd be careful with the windows repair option for now - it tends to wipe out grub...

---

### Post by caljohnsmith on 2009-02-18
For one thing it looks like you need to modify your Windows Grub entry, because normally you need to use Grub's "mapping" technique in order to boot Windows from a drive that is not first in the BIOS boot order. Therefore, I think your Windows entry should be:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
But getting a "disk read error" is usually due to other causes. In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

