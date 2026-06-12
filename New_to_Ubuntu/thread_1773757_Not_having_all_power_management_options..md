---
title: "Not having all power management options."
date: 2011-06-02
forum: New to Ubuntu
---

### Post by Xeneth on 2011-06-02
I had to reinstall Ubuntu because I didn't like Natty, but after reinstalling 10.10, I do not have all the power down options.  Specifically, I do not have the option to hibernate.  What's needed to add this?

---

### Post by dnairb on 2011-06-02
It's possible that the swap partition is not active, or not listed in fstab to automount on boot.

We need to check various system files and settings:

In terminal, run the following:

```
sudo blkid
```

This should give an output similar to the following (I have highlighted the relevant part):

```
/dev/sda1: LABEL="Root" UUID="df07187d-f140-4758-a621-9fdc4096e356" TYPE="ext4" 
/dev/sda2: LABEL="Home" UUID="6c602fd4-8303-481e-9112-2fbcfc76a1ff" TYPE="ext4" 
/dev/sda3: LABEL="Data" UUID="32b56d22-76dc-41df-96c0-d61d5b0ffc1f" TYPE="ext4" 
**/dev/sda4: UUID="[COLOR="Red"]2b37da11-ad70-4ccb-b090-cec4822b788c[/COLOR]" TYPE="swap" **
/dev/sdb1: LABEL="Backup" UUID="bf881b56-eed1-40a3-bc17-69e8116b0b55" TYPE="ext4"
```

Next we need to check fstab, to see the drive partitions that are automounted on boot. Again in terminal, run:

```
gksudo gedit /etc/fstab
```

This should give something similar to the following (again I have highlighted the relevant part):

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1
UUID=df07187d-f140-4758-a621-9fdc4096e356 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2
UUID=6c602fd4-8303-481e-9112-2fbcfc76a1ff /home           ext4    defaults        0       2
# /data on /dev/sda3
UUID=32b56d22-76dc-41df-96c0-d61d5b0ffc1f	/data	ext4	defaults	0	2
[B]# swap was on /dev/sda4
UUID=[COLOR="Red"]2b37da11-ad70-4ccb-b090-cec4822b788c[/COLOR] none            swap    sw              0       0[/B]
```

Next, we have to check a file that tells the system the location of the running snapshot taken when hibernating, so it can wake up. Again, in terminal, run:

```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

This should look something like this:

```
RESUME=UUID=[COLOR="Red"]2b37da11-ad70-4ccb-b090-cec4822b788c[/COLOR]
```

Note how all 3 of these report the same UUID for the swap.

If they differ on your system, you need to the edit the **/etc/fstab** and **/etc/initramfs-tools/conf.d/resume** files so that they contain the same UUID as reported by blkid above.

After doing this, if they do indeed differ, there is one final command to run to reconfigure the system to use the swap file. In terminal (for the final time):

```
sudo update-initramfs -u
```

then reboot.

---

### Post by Xeneth on 2011-06-02
```

sudo blkid
/dev/sda1: UUID="305f907d-ff30-4c77-b8ba-91bdb16fa87f" TYPE="ext4" 
/dev/sda5: UUID="f2b0f33d-8149-40f6-b9b7-cce29eb25e2e" TYPE="ext4" 

```As you can see, no swap partition is showing.  I thought this odd so I went to /dev/ to see if there was something there, and found sda2 is not mounted.  I do not know the command to check if this is my swap partition, or any details about this partition, but I am betting.

EDIT:
```

/dev$ sudo fdisk -l sda

Disk sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc5f3

Device Boot      Start         End      Blocks   Id  System
  sda1   *           1        1824    14647296   83  Linux
  sda2            1824        7296    43955201    5  Extended
  sda5            1824        7296    43955200   83  Linux

```It would appear a swap partition did not get created.  I'm not sure how that happened.

I can save home data to my server and repartition sda2 into a smaller bit, then make what's left into a swap.

Thanks.  Never would have known the reason without you.

---

### Post by dnairb on 2011-06-03
> **Xeneth said:**
> Thanks.  Never would have known the reason without you.

You're welcome.

---

### Post by JohnBonne on 2011-06-03
When the OP gets his problem solved, I have a question pertaining to the swap file. I have notices there is no swap file usage and since reading this, have to ask for help. my configuration looks "different".
```
sudo blkid
```:
/dev/loop0: UUID="78629ec4-38a6-42a2-a178-eb42d848e65f" TYPE="ext4" 
/dev/sda1: UUID="BA80A07680A03B31" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="5A18F4B818F4946B" TYPE="ntfs" 
/dev/sdb1: LABEL="Ubuntu" UUID="EA1A6F681A6F312D" TYPE="ntfs" 
/dev/sdb2: UUID="01CBD0945E4134E0" TYPE="ntfs" 

```
gedit /etc/fstab
```
 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

I wonder if I have a swap file and if this impacts performance.

---

