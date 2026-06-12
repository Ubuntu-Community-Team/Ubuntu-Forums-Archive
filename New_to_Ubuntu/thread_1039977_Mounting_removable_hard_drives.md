---
title: "Mounting removable hard drives"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by aireq on 2009-01-15
I have many removable SATA hard drives that slide into a set of slots in the front of my computer. I'm new to linux and trying to figure out how setup my FSTAB file properly. 

**Question 1**
I'd like each drive to retain it's name. Just to make things simple I'm just going to name the drives driveA, driveB, driveC etc etc. etc..

So I'm going to add entries into FSTAB using the UUID of each drive.

Is the UUID generated from the hardware, or will it change if I format/partition the drive? These drives are NTFS now so I'll have to format them.

**Question 2**
I've mounted one of these drives manually using the following command

sudo mount -t ntfs-36 /dev/sde1 /media/driveA

before doing that I had to create the driveA directory by typing

sudo mkdir /media/driveA

So what happens if I add files to /media/driveA when the drive is not mounted? Does that mean I'm putting files on the root partion under the media/driveA folder? What happens if remount the drive? Will the folder contain files from both partition? What if there is a naming conflict?

**Question 3**
After I mount the drive I can access it's contents fine from /media/driveA. However on the left side of the file browser window I see an icon for the drive. If I double click it it asks me to mount the drive again. Is this because I haven't setup the Fstab file and just mounted the drive by hand?

---

### Post by Bucky Ball on 2009-01-15
Did you logout and back in again? Restart? ... after changing the fstab?

---

### Post by cdtech on 2009-01-15
USB devices are auto mounted using HAL and the /media directory. Once the device is plugged in, HAL will try to detect the device using the device label or by /dev (sda6) if no label, it then creates a directory within /media/devicelabel and mounts the device for you. By using the /media directory the device will show up on your desktop as a mounted external device. Once the device is unplugged the directory is gone so trying to save or write to that directory will only produce an error.

I use external partitions mounted through /etc/fstab within /media directories I've created so they are viewable on the desktop. Others I create a folder within the /mnt directory to mount them so their not viewable on the desktop.

If you create a directory within /media and write to that directory with the device unmounted it will save to that directory, but when you mount the device it will overwrite any existing thing within the directory.

---

