---
title: "What is exact procedure to remove 10.04 and install 10.10 ?"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Rushyang on 2010-12-08
Hiya fellas!

I assigned little less hdd space in my laptop for ubuntu 10.04. I'm on dual boot with windows 7 and ubuntu 10.04 ... 

Now I would like to remove ubuntu 10.04 completely so that I can assign more partition space through windows sofwares... & then install ubuntu 10.10 in it.. What steps should I follow? This is because I'm confused in order to remove / overwrite grub 2.

---

### Post by Ustonkey on 2010-12-08
Why not just update it?
 Stonkey

---

### Post by kesman on 2010-12-08
If you already have partitioning tools installed in Windows, just boot into it and delete the partition containing Ubuntu 10.04.

Then run the defragment tool to the partition containing Windows and then resize the Windows partition. I've had some problems resizing partitions containing operating systems, so I would recommend taking some backups if you have all your personal stuff in the same partition as the OS.

After resizing, just boot with Ubuntu 10.10 cd or usb stick and install it to the unallocated space (removed partition). It will rewrite the grub and detect Windows automatically.

---

### Post by coffeecat on 2010-12-08
> **Rushyang said:**
> Now I would like to remove ubuntu 10.04 completely so that I can assign more partition space through windows sofwares... & then install ubuntu 10.10 in it.. 

Don't remove the Ubuntu 10.04 partition yet, otherwise you will make grub non-functional and you won't be able to boot Windows. Also, don't create partitions for Ubuntu in Windows. Windows cannot create Linux filesystems.

This is what I suggest you do. Boot into Windows and use its Disk Manager to shrink the Windows C: drive by as much space as you want to give to Ubuntu. This will leave unallocated space between Windows and Ubuntu. Then you can boot into the Ubuntu live CD and use Gparted to rearrange your Linux partition prior to reinstalling.

---

### Post by kesman on 2010-12-08
> **coffeecat said:**
> Don't remove the Ubuntu 10.04 partition yet, otherwise you will make grub non-functional and you won't be able to boot Windows.

Grub isn't located in the Ubuntu partition, it's written in the MBR record, so deleting the Ubuntu partition won't effect in it.
Of course choosing Ubuntu from the Grub -menu will result in an error because it refers to a deleted location. Booting Windows from Grub will still work normally.

**EDIT: I stand corrected, sorry for the misleading information in this post.**

---

### Post by coffeecat on 2010-12-08
> **kesman said:**
> Grub isn't located in the Ubuntu partition, it's written in the MBR record, so deleting the Ubuntu partition won't effect in it.
Of course choosing Ubuntu from the Grub -menu will result in an error because it refers to a deleted location. Booting Windows from Grub will still work normally.

No it won't Please read up on grub. Grub stage 1 only is installed to the mbr. Further code is written to the embedding area, but grub stage 2 and all the grub configuration files, including the all-important grub.cfg are in the Ubuntu root partition. If you delete the Ubuntu root partition you will get a grub error and you will not be able to boot anything.

---

### Post by owiknowi on 2010-12-08
First back up your files from /home/yourname/ and even from ms w7 (just in case).

Depending on your current partitioning a possible way is the following.
1. Boot from a GParted or PMagic CD.
2. Delete the partitions with Linux (Swap and ext 3/4?)
3. Select the ms w7 partition (ntfs?) and resize to your liking.
4. Create minimal two partitions in the residing free space: one for / and one for swap (4GB or 4096MB).
5. Reboot with Ubuntu 10.10 installation CD and install it.
The MBR will be overwritten with the new boot loader.

BTW. It's saver to create a separate /home partition for your files.
Thus you always can change your Linux.

You also can try this from within w7 and with the Ubuntu 10.10 installation CD.

---

### Post by amjjawad on 2010-12-08
> **kesman said:**
> Grub isn't located in the Ubuntu partition, it's written in the MBR record, so deleting the Ubuntu partition won't effect in it.


Please check the two links below:

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

[https://help.ubuntu.com/community/Grub2#File%20Structure](https://help.ubuntu.com/community/Grub2#File%20Structure)

---

