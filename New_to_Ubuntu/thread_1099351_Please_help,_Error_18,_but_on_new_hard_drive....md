---
title: "Please help, Error 18, but on new hard drive...?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by thatryan on 2009-03-18
I have downloaded the latest 8.10 and am trying to install on a brand new hard drive.  320 GB so I know there is space.  I ran the guided setup using entire drive, so it was automatic, I got through the entire install process, and it ejected my CD saying to remove it so it will boot into OS.
Upon reboot it gets to GRUB loading screen then gives error 18.
I do not understand why or what could be cause.  
Any ideas?  Please advise, thanks!

---

### Post by overdrank on 2009-03-18
Hi and welcome, are there any other operating systems on other drives in the system?
You did not see a error about the grub install during the installation?

---

### Post by muteXe on 2009-03-18
[http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)

"Error 18: Selected cylinder exceeds maximum supported by BIOS 

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel. "

No idea what it means, but hope it helps :)

---

### Post by tsali on 2009-03-18
> **muteXe said:**
> [http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)

"Error 18: Selected cylinder exceeds maximum supported by BIOS 

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel. "

No idea what it means, but hope it helps :)

It means that you have to install grub to the MBR instead of root.

---

### Post by muteXe on 2009-03-18
See, why didn't they put it like that eh? :D

---

### Post by thatryan on 2009-03-18
No there is nothing on the hard drive at all, I just unwrapped it, which is why it confused me because I read that about the selected cylinder being beyond BIOS reach...

---

### Post by Malalo on 2009-03-18
I had the same problem and the way to solve it is, when your install (you'll have to start over), you select the manual partitioning. When you create the partitions, create one at the beginning of the drive mounted on "/boot". This always solved the problem for me.

---

### Post by thatryan on 2009-03-18
I don't know how to do it manually.   What size, name and types do I make all the partitions?

---

### Post by Malalo on 2009-03-18
Reinstall from scratch. When you get to the partitioning phase, you'll have different options, manual, automatic, etc. Select Manual (I don't have the exact option names, if someone could help here) and "entire disc". I suggest "entire disc" since you mentioned that no other OS is installed on your disc. 
When you get to the "manual partitioning" section, you'll be able to create partitions on your disc as you wish them to be. You can create a 512 Mb partition (largely enough) mounted as /boot (type "/boot" in the "mount point" field) . As for the rest, up to you, but do remember to create a swap partition.

---

### Post by mikechant on 2009-03-18
It's always a good idea to have a seperate /home partition - it makes upgrades (and other operations) easier. Your root partition (shown as mount point / ) should probably be 10Gb. If you 512Mb or less of memory, your swap space should be 2x memory size; if you have 1Gb or more of memory then you probably want space space equal to memory size.
So if you had 2Gb of RAM, one possible layout would be:
1st primary partition: mount point /boot, type = ext3, size = 200Mb
2nd primary partition: mount point none, type = swap, size = 2Gb 
3rd primary partition: mount point /, type = ext3, size = 10Gb
4th primary partition: mount point /home, type = ext3, size = rest of disc
(The mount point, type, and space allocation are the basic things you need to specify for each partition during the install).

This is a simple layout but not very flexible; if you wanted to install another OS or have a seperate partition for (say) movies and music, you couldn't because you are only allowed 4 primary partitions.
For a more flexible layout, you could have the 1st (boot) partition as above, then define the 2nd partition as an extended partition containing 3 logical partitions for swap, root (/), and /home, possibly leaving unallocated space at the end.

Anyhow, you don't have to worry too much about messing it up, since you are doing a fresh install with no data on the disc that matters if you lose it.

---

