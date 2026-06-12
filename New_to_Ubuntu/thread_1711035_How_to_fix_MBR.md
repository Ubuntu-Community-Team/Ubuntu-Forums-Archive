---
title: "How to fix MBR?"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by Fanatico on 2011-03-20
I have computer which runs Ubuntu 10.04 which has built in SD card slot. I have 8GB SDHC card with installed Ubuntu.

I need to clone Ubuntu from 8GB SDHC card into 4GB SDHC card. The actual size of data is less then 3GB so there is no problem here.

I manually created 2 partitions boot and root and successfully copied all content from 8GB SDHC card into 4GB SDHC card.

The only problem remained how to fix MBR, because obviously target 4GB SDHC doesn't boot.

Can anyone advise?

Thanks

---

### Post by tordeu on 2011-03-20
You can make a partition bootable using the Disk Utility at System > Administration > Disk Utility.

That will not be enough, because the UUID of your new partition is different. You need to run
```

sudo blkid

```

This will list the UUIDs of all partitions. You need to find the UUID of the new boot partition and then edit the /etc/fstab on your new root partition and change the UUID of the boot partition which is currently there to match the UUID of the new boot partition.


What you could have done (and could still do) when migrating your system is to:
1. install a fresh Ubuntu on the new card, 
2. save the /etc/fstab on that new drive
3. copy all the data from the old drive to the new drive
4. copy the fstab back

---

### Post by Fanatico on 2011-03-21
I think you misunderstand my question. I was asking about about fixing MBR (master boot record). The fstab file comes into play much later, as far as I understand.

Thanks

---

### Post by xumuk37 on 2011-03-21
Take a look on 'dd' tool in google... It clones entire devices, and this what you want, as I think...

---

### Post by Fanatico on 2011-03-21
dd won't help me because in my case source and destination has different sizes and I have to fix MBR. This is exactly what I am asking about!

---

### Post by wilee-nilee on 2011-03-21
This is a wiki on reinstalling grub2 to the mbr from a live cd=10.04 in your case. 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by tordeu on 2011-03-21
No, I did not misunderstand your question. The steps I provided were just meant as a general possibility how you could migrate from one card to another, because this way most things (partitions/bootable device) will already be setup for you.

What you need to do is actually do install grub. To do that you need to boot either from a CD or from your old card, although I would recommend to boot from a CD, because this way it will be impossible for you to accidentally destroy something.

So, let's assume you boot from CD and have your new card put in as well.

1.
Go to System > Administration > Disk Utility and find out which device your new card is (select the device on the left side and then on the right side you will see information about that card. One thing will say something like "Device: /dev/sda" or something similar. This is what we need).

2.
Disk utility will also show you visually the partitions you created. Click on the boot partition and then click on "Mount Partition"

3.
Under the visual presentation of the partitions (with the /boot partition selected) you will now also see the "Mount point" of the boot device (something like /media/<UUID>; instead of <UUID> it will have a lot of numbers, probably))

4.
Now open a terminal and do (substitute <UUID> with the numbers it shows you in disk utility)
```

cd /media/<UUID>

```5. type
```

ls

```It should not show you some files (like initrd.img and stuff like that)

6. Now install grub like this:
substitute <UUID> with your UUID again
substitute <DEVICE> with the Device that the Disk Utility displayed (might be something like sda or sdb or sdc)
```

sudo grub-install --root-directory=/media/<UUID> /dev/<DEVICE>

```Just as an example: This could look like this:
```

sudo grub-install --root-directory=/media/55e6073e-9fdf-4e5e-8f0c-d954e164c9ab /dev/sda

```

EDIT: I was too slow ;-)

---

### Post by wilee-nilee on 2011-03-21
I would also suggest getting acquainted with supergrub it is very good for getting into OS's that wont boot to work from the inside. The middle one is what I use I do the repairs myself. It will also get you into windows as well.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by C.S.Cameron on 2011-03-21
I have used dd in such a case, had to shrink the partition using gparted, and re-expand it later.
Made a nice bootable clone.

---

### Post by arvevans on 2011-03-21
fdisk /mbr

---

### Post by gandaran on 2011-03-22
> How to fix MBR?
easiest is with the [rescatux]("http://www.supergrubdisk.org/") disk

---

### Post by wizard10000 on 2011-03-22
> **Fanatico said:**
> dd won't help me because in my case source and destination has different sizes and I have to fix MBR. This is exactly what I am asking about!

Actually it would.

First, copy the boot sector to a file.  Assuming the SD cards are /dev/sdb, insert the 8GB card and do this -

```
sudo dd if=/dev/sdb of=/tmp/mbrsdb.bak bs=512 count=1
```

then unmount the 8GB card, mount the 4GB card (also /dev/sdb) and do this -

```
sudo dd if=/tmp/mbrsdb.bak of=/dev/sdb bs=446 count=1
```

This will overwrite the MBR of the SD card without overwriting the partition table.  The first 446 bytes of the boot sector are the MBR, the next 64 bytes are the partition table and the remaining two bytes are signature bytes.  If you want to install an MBR without altering a partition table you use dd to copy the source boot sector to a file, then use it again to copy the first 446 bytes to the target device.  

If the devices are identical (same size and same partition table) then you can just copy all 512 bytes.

edit:  You'd still have to set the boot flag on the 4GB card but that's pretty easy.

---

### Post by Fanatico on 2011-03-22
wizard10000, thank you for your response.

Well, I tried in the past to copy 446 bytes of MBR as you described. Unfortunately it doesn't work. Attempt to boot newly created card led to exception.

As far as I understand these 446 bytes contain bootstrap code which execute jump to boot partition: stage1.5, stage 2 of grub etc. Since location of boot partition also changed ( I relocated it from bigger to smaller card) the bootstrap code jumps to wrong location and I get exception. That's why I've asked how to fix MBR (actually addresses inside MBR where to jump).

Please correct me if I am wrong.

---

### Post by wep940 on 2011-03-22
Follow the advice for installing grub - it will set that all up for you.

---

### Post by wizard10000 on 2011-03-22
> **Fanatico said:**
> wizard10000, thank you for your response.

Well, I tried in the past to copy 446 bytes of MBR as you described. Unfortunately it doesn't work. Attempt to boot newly created card led to exception.

As far as I understand these 446 bytes contain bootstrap code which execute jump to boot partition: stage1.5, stage 2 of grub etc. Since location of boot partition also changed ( I relocated it from bigger to smaller card) the bootstrap code jumps to wrong location and I get exception. That's why I've asked how to fix MBR (actually addresses inside MBR where to jump).

Please correct me if I am wrong.

If the bootable partition *number* is the same it should work, although as I said you also have to set the boot flag on the partition.  As others have said reinstalling grub should also get you where you need to be.

---

