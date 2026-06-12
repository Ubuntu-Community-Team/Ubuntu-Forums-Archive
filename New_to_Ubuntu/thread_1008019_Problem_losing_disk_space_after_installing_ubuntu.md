---
title: "Problem losing disk space after installing ubuntu"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by dgg9879 on 2008-12-11
I recently installed ubuntu just for surfing the internet (8.04) so I have a dual boot. I now have 2 partitions on my disk drive that I can't access and when I go into control panel - administrative tools - storage - device management it says there is another operating system on them when I try to format them so I don't want to do this but I would like to get the partitions back.

To further complicate matters, I had windows XP installed by a pc shop because I lost my disk. I couldn't activate the shop installed one since I did not have the right product key. Then I found my Windows XP disk and installed it. Now I have 2 windows XPs to choose from when I boot up.

I've lost about 200BG out of 750gb space and I can do without it.

I'm just wondering if I have any options apart from re-starting again - re-formatting and re-installing both operating systems, which I don't really want to do.

I used macrium to backup the original windows install with all my drivers and programs included but I've never restored from it and not confident it would work, especially if I changed the disk partition structure.

Have no backup of Linux and don't even know where it is on my pc.

It would be good to know how to install ubuntu to a particular partition or drive.

I would also like to know how to make it so the default boot up is windows instead of linux, or better still, not to boot into anything until I make a choice and power off if no choice is made after 5 min or so. Is it possible to make such as change post-installation?

---

### Post by vishal_mala on 2008-12-11
I advice u to reformat and repartion your drive, and b carefull for the 2nd time, that the only vaible soluion. And yes before commiting this wai to see what others have to comment. Altenatively u can copy your important files into usb or something through the live cd. And yes bfore formatting check wether u have something important in my documents area ( I recently lost many things in there).

---

### Post by Michael.Godawski on 2008-12-11
hey dgg9879, 

can you please run in terminal:
```
sudo fdisk -l
```
post the output here, and tell us which partitions you cannot access?

---

### Post by nhasian on 2008-12-11
> **dgg9879 said:**
> I now have 2 partitions on my disk drive that I can't access and when I go into control panel - administrative tools - storage - device management

Yep that sounds right to me.  There will the partition for the root linux filesystem / and another parition for swap.  Windows cannot access the EXT3 partition without installing 3rd party software like [EXT2IFS]("http://www.fs-driver.org/")

[QUOTE=dgg9879]Now I have 2 windows XPs to choose from when I boot up.[/QUOTE]

If you installed windows into the same directory as before then you can just edit the bootup menu and remove the duplicate line.


[QUOTE=dgg9879]Have no backup of Linux and don't even know where it is on my pc.[/QUOTE]

This one is easy.  in ubuntu open a terminal and type:

```
sudo fdisk -l
```

this will show you all your drives and how they are partitioned.  the HPFS/NTFS would be your windows parition and then you can also see the Linux and swap partitions. Under Device Boot you can see which drive/partition it is.  /dev/sda1 would be the first serial ATA drive, 1st partition.  /dev/sda2 would be 2nd partition, /dev/sdb1 is the 2nd drive first partition and so on.

[QUOTE=dgg9879]It would be good to know how to install ubuntu to a particular partition or drive.[/QUOTE]

the above information from fdisk should give you the information you need.  during the ubuntu installation if you click on the manual partitioning you will have more control over where everything is installed to.

[QUOTE=dgg9879]I would also like to know how to make it so the default boot up is windows instead of linux, or better still, not to boot into anything until I make a choice and power off if no choice is made after 5 min or so. Is it possible to make such as change post-installation?[/QUOTE]

to make windows boot first & change the timeout you need to edit the grub menu with:

```
sudo gedit /etc/boot/grub/menu.lst
```

you can change how long it waits with the timeout value.

you can also change the order of operating systems by moving them up or down in the list.  be sure to make a copy for a backup of the file first in case you muck something up :)

---

