---
title: "Help reinstalling grub on logical Partition."
date: 2011-02-17
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-02-17
I reisntalled windows and that overwrote my grub2 bootloader.  I want to reinstall grub2 but i cant find/mount my ubuntu partition. My ubuntu partition is a logical partition /dev/sdb5 and i cant figure out how to mount it. How can i do this? Thanks

---

### Post by hunter99507 on 2011-02-17
So i found my UDID by typing blkid, but now how do i mount the disk?

---

### Post by wilee-nilee on 2011-02-17
> **hunter99507 said:**
> I reisntalled windows and that overwrote my grub2 bootloader.  I want to reinstall grub2 but i cant find/mount my ubuntu partition. My ubuntu partition is a logical partition /dev/sdb5 and i cant figure out how to mount it. How can i do this? Thanks

Grub goes to the mbr not the partition, unless your using a 3rd party bootloader like easybcd. Post the out put of this command from a booted live ubuntu cd.
sudo fdisk -lu

Here is a link on reloading it from the live cd if you want to just do it yourse3lf.:)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

So if your Ubuntu partition is actually /dev/sdb5 it is likely that grub should be installed to sdb. You can also run the bootscript in my signature and post the output in code tags for a what is where picture of your setup.

---

### Post by hunter99507 on 2011-02-17
I am using easy BCD so i beleve i would need to install to a partition (sdb5)

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50a5b170

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    25167871    12582912    7  HPFS/NTFS
/dev/sdb2   *    25173855   304179197   139502671+   7  HPFS/NTFS
/dev/sdb3       304179198   617705471   156763137    5  Extended
/dev/sdb4       617707520   625141759     3717120   12  Compaq diagnostics
/dev/sdb5       304179200   352608255    24214528   83  Linux
/dev/sdb6       352610304   356593663     1991680   82  Linux swap / Solaris
/dev/sdb7       356594868   617699249   130552191    7  HPFS/NTFS

Disk /dev/sdc: 4075 MB, 4075290624 bytes
126 heads, 62 sectors/track, 1018 cylinders, total 7959552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e87d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3223366752  3470046675   123339962   f4  SpeedStor
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(793, 22, 13) logical=(412617, 44, 21)
Partition 1 has different physical/logical endings:
     phys=(870, 235, 61) logical=(444194, 50, 48)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   378192737   710426324   166116794   10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(48411, 96, 54)
Partition 2 has different physical/logical endings:
     phys=(870, 235, 50) logical=(90940, 49, 7)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225603442   225603451           5   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(367, 66, 47) logical=(28879, 11, 13)
Partition 3 has different physical/logical endings:
     phys=(370, 32, 37) logical=(28879, 11, 22)
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by wilee-nilee on 2011-02-17
As far as I know easybcd will read the sdb5 boot without any reinstall of grub. It just reads the sdb5 grub there already.

If you want it to work right now just put grub in the mbr, if it doesn't work put the MS bootloader back in this is very easy stuff. You have the grub2 link already, the command for reloading the MS to the MBR from the command line in repair on the install or recovery booted Windows media.
bootrec.exe /fixmbr

In my opinion you don't need easybcd, as you may now realize that loading the mbr is 1 or 2 commands depending on the OS. Use what you want though.

---

### Post by hunter99507 on 2011-02-17
For some reason GRUB2 on sdb5 isnt working. When i click "ubuntu" on easy bcd usually it takes me to the grub loader. When i click ubuntu on easy bcd it takes me to grub rescue, so i need to install grub2 on sdb5.  My issue it im new at this and i cant mount my sdb5 partition. Usually i find my partition in the menu on the ubuntu live cd but now its not showing, just my data drive (D partition sdb7). 

So how do i reinstall grub onto my sdb5 parition? I cant figure out how to mount it. Thank you.

---

### Post by wilee-nilee on 2011-02-17
> **hunter99507 said:**
> For some reason GRUB2 on sdb5 isnt working. When i click "ubuntu" on easy bcd usually it takes me to the grub loader. When i click ubuntu on easy bcd it takes me to grub rescue, so i need to install grub2 on sdb5.  My issue it im new at this and i cant mount my sdb5 partition. Usually i find my partition in the menu on the ubuntu live cd but now its not showing, just my data drive (D partition sdb7). 

So how do i reinstall grub onto my sdb5 parition? I cant figure out how to mount it. Thank you.

So when the easybcd takes you to grub can you boot into ubuntu?

Are you trying to bypass the grub menu?

---

### Post by hunter99507 on 2011-02-17
What "used" to happen is easy bcd would pop up. I would click ubuntu. After i click ubuntu it would bring me to grub2, from there i would click ubuntu and it would load ubuntu.

I messed something up so now i need to install grub2

Now what happens is easy BCD pops up. I click ubuntu like normal, after i click ubuntu (on easy bcd) it loads grub rescue. I need to reinstall grub2 on the sdb5 partition. it is a logical partition and i cant seem to mount it. How do i fix this?

---

### Post by ajgreeny on 2011-02-17
You should still be able to use the information in the link given by wilee-nilee, [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) but the final command should be changed to ```
sudo grub-install --root-directory=/mnt /dev/sda5
```assuming you are correct about the sda5 being the ubuntu partition.  Normally, as you can see grub is put on the first sector of the disk, not in a partition, so you need to edit the command from sda to sda5, but it should still work.

I must hasten to add that I have never used eastbcd, and can see no obvious reason why anybody would if they are serious about using a Linux distro, as grub appears to do a much better job of dealing with multiboot systems.

---

### Post by hunter99507 on 2011-02-17
So i got grub2 reinstalled, but when grub2 boots up it says i cannot find any partitions.  How do i fix this?

---

### Post by oldfred on 2011-02-17
Post this, so we can give better recommendatations:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

