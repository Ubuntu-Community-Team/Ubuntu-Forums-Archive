---
title: "Rebuild grub menu from working install?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2009-02-17
Hi, I accidentally kept my version of menu.lst after the latest kernel update.  Of course this means the latest kernel does not show up in the boot menu.  

I don't know how to create an entry manually, so I was wondering how I get grub to remake menu.lst based on the kernels (and Windows install) I have on this machine?

Thanks!

---

### Post by drs305 on 2009-02-17
Open menu.lst for editing, copy the top entry, make the changes reflect the new kernel information and save. Normally that is all it will take if all you have done is add a new kernel (which would by default install to the same drive/directory as your previous kernels).

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst
gksudo gedit /boot/grub/menu.lst

```

Replace the bold items:
```

title		Ubuntu 8.10, kernel 2.6.27**-11**-generic
uuid		ba83d184-705e-4115-9d42-0823c698a757
kernel		/boot/vmlinuz-2.6.27-**11**-generic root=UUID=ba83d184-705e-4115-9d42-0823c698a757 ro splash quiet 
initrd		/boot/initrd.img-2.6.27-**11**-generic
quiet

```

The non-bold items do not have to match the above since my preferences may be different. If you copy your previous top entry just change the bold items to match the new kernel number.

---

### Post by Hospadar on 2009-02-17
I believe you can also just ```
sudo update-grub
```
please though, backup your menu.lst file before you do this, and it would be a good idea to ```
man update-grub
``` and google update grub first if you are in doubt that is what you want.

---

### Post by Nixie Pixel on 2009-02-22
Thanks for the help - I couldn't get it to automatically rebuild, but I was able to manually edit the file thanks to drs305's suggestion.

Now I am going to re-install Windows on the primary boot partition, and I usually re-format when I re-install, to avoid nasty little Windows hooks being left behind (ok, I'm paranoid).

Knowing I am about to do this, is there anything I can do to prevent my bootloader becoming borked by the re-installation process?

Thanks!

---

### Post by caljohnsmith on 2009-02-22
Whenever you reinstall Windows, it will overwrite Grub in the MBR (Master Boot Record) with its own boot code so that the computer will boot straight into Windows after that. Fortunately reinstalling Grub to the MBR is easy, you can do it with these directions for instance:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Also, I think it is worth mentioning that I've seen many cases in the forums now of Windows slightly corrupting the HDD's partition table when you install Windows on a HDD with Linux partitions. I think that might be because there are at least two different standards for how to set up extended partitions and the logical partitions that go inside of them, and Windows probably uses the more restrictive standard, whereas most Linux partitioning tools use the other standard that allows more freedom in setting up the extended partition. Therefore, the Windows partitioner can't correctly deal with the logical partitions that have been set up in linux in some cases, and Windows ends up corrupting the partition table with its own rules. So the bottom line is, once you are done installing Windows, I would recommend posting back here:
```
sudo fdisk -lu
sudo sfdisk -d
```
So we can check that your partition table is OK. That's just a suggestion though, it's up to you.

---

### Post by Nixie Pixel on 2009-02-23
Thanks for the offer, here are the results:

```
sudo fdisk -lu

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb978e9cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2        83891430   145211534    30660052+   5  Extended
/dev/sda5       137211165   145211534     4000185   82  Linux swap / Solaris
/dev/sda6        83891556   117643994    16876219+  83  Linux
/dev/sda7       117644058   137195099     9775521   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa73fa73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   245762369   122881153+   7  HPFS/NTFS
/dev/sdb2       245762370   976768064   365502847+   5  Extended
/dev/sdb5       245762433   976768064   365502816   83  Linux
```

```
sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 83891367, Id= 7, bootable
/dev/sda2 : start= 83891430, size= 61320105, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=137211165, size=  8000370, Id=82
/dev/sda6 : start= 83891556, size= 33752439, Id=83
/dev/sda7 : start=117644058, size= 19551042, Id=83
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=245762307, Id= 7
/dev/sdb2 : start=245762370, size=731005695, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=245762433, size=731005632, Id=83
```

---

### Post by sahabcse on 2009-02-23
Hi

Follow the below url for rebuild the grub

------------------------------------------
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
===========================================

Regards,
Sahab

---

### Post by caljohnsmith on 2009-02-23
That's great, your partition table looks fine, Nixie Pixel. It appears your Windows reinstallation went smoothly; if you have any more problems, let us know, otherwise cheers and enjoy your dual-boot setup. :)

---

### Post by Nixie Pixel on 2009-02-23
Thanks for checking - for future reference, how would I know if there is an issue with the partition table?  I do tend to install/re-install operating systems relatively frequently, so it would be good to know.

---

### Post by caljohnsmith on 2009-02-23
> **Nixie Pixel said:**
> Thanks for checking - for future reference, how would I know if there is an issue with the partition table?  I do tend to install/re-install operating systems relatively frequently, so it would be good to know.
In order to detect partition table problems, I would recommend doing the following commands:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
If the first fdisk command ever says "omitting empty partition (X)" at the beginning of its listing of your drive, know for certain that your partition table needs fixing. Also, if the second parted command does not list your partitions but instead returns an error like "overlapping partitions" (or any other error), then that's the other sure sign that your partition table needs to be repaired. Hopefully you won't ever have any problems with your partition table, but if you do, feel free to post back to this thread if you would like help fixing it.

---

