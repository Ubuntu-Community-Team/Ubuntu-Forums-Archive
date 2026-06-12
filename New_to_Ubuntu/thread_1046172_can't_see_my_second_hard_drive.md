---
title: "can't see my second hard drive?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by craftiegracie on 2009-01-21
Hello!

   I am an absolute beginner and I need help.  I was tired of windows constantly crashing so I finally gave in and decided to make the switch to Linux cold turkey.  My main concerns are being able to run software I use for design projects and for my husband not to be confused.  When we were running windows, I installed an old hard drive as our 2nd one and we saved all our files to that hard drive.  It has never popped up as accessible and I'm not sure how to make Ubuntu see it so I can mount it and I'm not sure how to search for it.  I have this sneaky feeling that I may have reformatted that hard drive and installed ubuntu over my files in my zest to make the switch :(

Help?
Grace

---

### Post by nothingspecial on 2009-01-21
In your menus go to accessories > terminal.

Type ```
sudo fdisk -l
```

Paste what it says in a new post here.

---

### Post by craftiegracie on 2009-01-21
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8efdbd5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4270f76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18749   150601311   83  Linux
/dev/sdb2           18750       19457     5687010    5  Extended
/dev/sdb5           18750       19457     5686978+  82  Linux swap / Solaris



I noticed from other threads and boards that it will show cdroms as hard drives - I have 2 of those. . .so 2 hard drives and 2 cdroms plugged in plus my pda was plugged in charging at the moment - I don't know if that will show up too

---

### Post by craftiegracie on 2009-01-21
also, if I'm reading that right - there are 2 hard drives showing up - one is 200 GB and the other 160GB and linux is on the smaller one, right?

Thank you so much!

---

### Post by boof1988 on 2009-01-21
> **craftiegracie said:**
> also, if I'm reading that right - there are 2 hard drives showing up - one is 200 GB and the other 160GB and linux is on the smaller one, right?

Thank you so much!

I believe you are correct... Linux appears to be on the 160GiB HDD.  If that is the drive that had your important data on it, you may be able to recover some of the data using "testdisk" or some other recovery utility.  I don't have any experience with recovery utilities so I can't help much with the details.  The only thing (I believe) I know is that the drive has to be unmounted to run testdisk on it.  So you may need to use a LiveCD or something if you choose to go that path.

Hope this helps some...

---

### Post by craftiegracie on 2009-01-21
Thanks!  I'll have to think about it while I'm at work today and see what I can do this evening.

---

### Post by vanadium on 2009-01-21
The most likely cause of your problem is simple and not severe. Likely, your ntfs volume was not properly "closed" by Windows. In that case, Linux will refuse to auto-mount it.

Since you opted to remove Windows altogether, you will probably need to change the format of the drive anyway. ntfs is only partly supported under Linux. In particular, Linux can not fully check and repair a damaged volume.

Before changing the drive's format, you obviously want to safeguard your data elsewhere, and for that you need to be able to mount the drive. This will require a little bit of terminal work. Open a command line terminal and type (copy/paste from here)

```

cd && mkdir ntfs
sudo mount -t ntfs -o force,ro /dev/sda1 ntfs

```

The first command makes a directory "ntfs" in your home directory.

The second command involves using the sudo command: you need super user (administrator) privileges. The system therefore asks your pasword. This is your normal login password. While you are typing your password, you do not see anything appearing on the screen: this is normal.

You better copy commands and output you have back over here so we can see if all is normal.

If all is good, you should be able to use the file manager Nautilus to browse into the directory "ntfs" and see all of your files. You will not be able to write. Just copy the files you need into safety on another medium. Once the data are in safety, you can reformat the drive to a better file system for use with Ubuntu.

---

### Post by drubin on 2009-01-21
> **vanadium said:**
> 
```

cd && mkdir ntfs
sudo mount -t ntfs -o force,ro /dev/sda1 ntfs

```


Why not just install ntfs-3g. This provides a GUI method to mount the drive.

also using the force option by default?

---

### Post by vanadium on 2009-01-22
Dear Drubin

We have a user here who does not have Windows anymore. In such a case, one should not be using ntfs, except perhaps for removable drives that can be connected to Windows systems from time to time.

What we are recommending here is to mount the ntfs drive one last time to copy the data elsewhere. After that, the drive can be reformatted to the ext3 filesystem, which is fully supported under Linux, and the data can be restored to a very reliable modern file system that can be maintained perfectly using only linux.

The drive currently does not auto-mount because it is not "clean". The only way to make it clean is by having it checked by Windows. Perhaps ntfsfix under Linux would also be sufficient, but ntfsfix is not a full replacement for the ntfs file checking tools under Windows. Results are therefore uncertain.

A possibility to mount an unclean ntfs volume anyway is by using the -o force option. You should NEVER routinely "force" mount an ntfs volume. You should NEVER include that option in your /etc/fstab (unless you do not care for the data, that is). Instead, you must either fix an unclean ntfs volume (sorry, but you need Windows for this) or reformat it altogether.

> Why not just install ntfs-3g
ntfs-3g is now the ntfs driver by default since recent Ubuntu version. You are referring to ntfsconfig, though, a graphical utility that can add ntfs volumes to /etc/fstab without the need for manually editing /etc/fstab. This is still not going to mount this partition because you do not address the issue causing the drive not to mount by default.

---

### Post by craftiegracie on 2009-01-22
ubuntu@ubuntu:~$ cd && mkdir ntfs
ubuntu@ubuntu:~$ sudo mount -t ntfs -o force,ro /dev/sda1 ntfs
Failed to read last sector (488392001): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ubuntu@ubuntu:~$

---

### Post by craftiegracie on 2009-01-22
I wasn't sure if I needed to do each line on it's own, so I did it again and got pretty much the same result. . .

ubuntu@ubuntu:~$ cd && mkdir ntfs
mkdir: cannot create directory `ntfs': File exists
ubuntu@ubuntu:~$ sudo mount -t ntfs -o force,ro /dev/sda1 ntfs
Failed to read last sector (488392001): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ubuntu@ubuntu:~$ 


Thank you!

---

### Post by vanadium on 2009-01-23
This looks bad. The output of "sudo fdisk -l" you showed clearly shows that /dev/sda1 is (was?) your ntfs partition. That is what the partition table still reports. The mount command, however, reports that no ntfs partition is found/recognized. It therefore looks as if it has been wiped indeed like you mentioned in the beginning. Yet your Ubuntu installation is on the other drive (sdb) and not on the drive containing the ntfs partition (sda).

If you do not have a backup of your data, you are in trouble. You could try recovery with the programs "testdisk" and "photorec", but I do not have any experience with these utilities.

If you have a backup, then just reformat /dev/sda1 to ext3 and use that as a data partition. We can help with the formatting and assigning proper permissions.

---

### Post by boof1988 on 2009-01-23
> **craftiegracie said:**
> also, if I'm reading that right - there are 2 hard drives showing up - one is 200 GB and the other 160GB and linux is on the smaller one, right?

Thank you so much!

It looks like Linux is installed on the 160GB Drive.  Is this the drive that had your Windoze on it?  And is there any very important data on it that you would like to try to recover?

Is the 200GB drive the one you added for data storage purposes (when you were running Windoze)?

If the 200GB drive is the one that has the data (you would like to keep), do you want some guidance on trying to recover the data?

If there is data that you want to recover from the drive, please remember that it is a good idea to stop using that drive until you recover what you can.

Let us know if this is a route you want to go.

---

### Post by oldschoolDebian on 2010-07-31
I am just curious if this problem has been solved.  From what i have been reading a part of the ntfs drive is missing.  Would it be better for her to use a live cd of Ubuntu to transfer what she can if possible.  with out changing the /etc/fstab information as of yet.  Since the user is new to the OS ( OS = operating system).  Changing the /fstab would be a bit advanced at this point.  more should be  looked at recovery of the data i would say?

just a thought..

---

