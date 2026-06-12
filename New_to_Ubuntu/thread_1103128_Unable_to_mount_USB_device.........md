---
title: "Unable to mount USB device........"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by blandman3 on 2009-03-22
How can I access My Documents, or any Windows folder, while using UBUNTU?

I have file sharing on, but no luck.

Also, I am unable to mount my usb device.  This particular device has MagicJack on it.  This is a program that enables me to have phone service using the usb port.  How can I get this program to run in ubuntu?

---

### Post by UnknownFear on 2009-03-22
> **blandman3 said:**
> How can I access My Documents, or any Windows folder, while using UBUNTU?
[http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/]("http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/")

---

### Post by drs305 on 2009-03-22
To access windows folders, install ntfs-config:
```

sudo apt-get update
sudo apt-get install ntfs-config

```
Run it from the Applications, System Tools, NTFS Configuration Tool or with:
```

sudo ntfs-config
```
Select "Enable write support" and, after clicking OK, type in the mount point. It will be created in /media and an entry for the ntfs partition will automatically be created in fstab.
Run this to mount the new mount point:
```

sudo mount -a

```

I am not familiar with MagicJack.

---

### Post by blandman3 on 2009-03-22
> **drs305 said:**
> 
I am not familiar with MagicJack.

I don't know if you have seen it on CNN or any commercial on television, but magicjack is a usb device that enables you to share the internet connection and use your telephone for only $20.00 a YEAR!  I found this to save me money over any other company-even your cable company!

This device automatically starts up with your computer, and runs its own program that makes it possible to use your usb port as a telephone port.

how can I fix this so that the application will run in ubuntu?

---

### Post by fabricator4 on 2009-03-22
> **blandman3 said:**
> How can I access My Documents, or any Windows folder, while using UBUNTU?

I have file sharing on, but no luck.

Also, I am unable to mount my usb device.  This particular device has MagicJack on it.  This is a program that enables me to have phone service using the usb port.  How can I get this program to run in ubuntu?

For MagikJack:
[http://www.broadbandreports.com/forum/r20977358-Successfully-setup-Ubuntu-Linux-VMWare-XP-MagicJack](http://www.broadbandreports.com/forum/r20977358-Successfully-setup-Ubuntu-Linux-VMWare-XP-MagicJack)

For accessing a folder on a windows machine see this recent thread:
[http://ubuntuforums.org/showthread.php?t=1102934](http://ubuntuforums.org/showthread.php?t=1102934)

Chris

---

### Post by blandman3 on 2009-03-22
compaqowner@ubuntu:~$ sudo mk dir windrive
[sudo] password for compaqowner: 
sudo: mk: command not found
compaqowner@ubuntu:~$ sudo mkdir windrive
compaqowner@ubuntu:~$ thebig28
bash: thebig28: command not found
compaqowner@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /mnt/windrive -o "umask=022"
ntfs-3g: Failed to access volume '/dev/hda1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
compaqowner@ubuntu:~$ /sbin/mount.ntfs --help

ntfs-3g 1.2506 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=,
          syncio.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
compaqowner@ubuntu:~$ 

This is what I get when I try using those commands.

How can I override this?  Am I doing it right?

---

### Post by drs305 on 2009-03-22
This command should mount it (if it's sda1), although I still recommend using ntfs-config for a permanent solution:
```

sudo mount -t ntfs /dev/sda1 /mnt/windrive -o umask=022

```

You can run this to see the available devices:
```

sudo fdisk -l

```

---

### Post by fabricator4 on 2009-03-22
> **fabricator4 said:**
> For MagikJack:
[http://www.broadbandreports.com/forum/r20977358-Successfully-setup-Ubuntu-Linux-VMWare-XP-MagicJack](http://www.broadbandreports.com/forum/r20977358-Successfully-setup-Ubuntu-Linux-VMWare-XP-MagicJack)

For accessing a folder on a windows machine see this recent thread:
[http://ubuntuforums.org/showthread.php?t=1102934](http://ubuntuforums.org/showthread.php?t=1102934)

Chris

In a classic case of cyclopsian myopia the thread I pointed you to was for accessing a shared folder on a windows machine on the same network via Samba.  If the Windows partition is in the same machine as your Ubuntu boot drive, that would be a completely different problem.

Chris.

---

### Post by blandman3 on 2009-03-22
Lol, yeah, I guess I mislead you-

I have dual boot with xp/ubuntu

what is the different story?

---

### Post by blandman3 on 2009-03-22
Here is what I get when I type:

sudo fdisk -l

compaqowner@ubuntu:~$ sudo fdisk -l
[sudo] password for compaqowner: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4f6e4f6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         617     4664488+   b  W95 FAT32
/dev/sda2   *         618       10336    73475640    7  HPFS/NTFS

Disk /dev/sdb: 18 MB, 18612224 bytes
1 heads, 36 sectors/track, 1009 cylinders
Units = cylinders of 36 * 512 = 18432 bytes
Disk identifier: 0x6f20736b

Disk /dev/sdb doesn't contain a valid partition table
compaqowner@ubuntu:~$ 

**What am I supposed to be looking at here?**

---

### Post by ronocdh on 2009-03-22
OP typed **mk dir** when the actual terminal command is **mkdir**. Perhaps that will help.

---

### Post by fabricator4 on 2009-03-22
> **blandman3 said:**
> Lol, yeah, I guess I mislead you-

I have dual boot with xp/ubuntu

what is the different story?

In that case, you have to mount it as others have suggested.  You ran fdisk to see what drives and partitions were there, and what they were called in Linux land.

In this case /dev/sda2 appears to be your NTFS partition.  The first partition is /dev/sda1 which _might_ be your Windows boot partition, however it appears be FAT32, not NTFS

You'll need to adjust the mount command according to which you require.  I'll leave others to suggest specific mount parameters because I don't have a dual boot machine here to play with.

Chris.

---

### Post by kansasnoob on 2009-03-22
If you install ntfsprogs you'll be able to access your ntfs partitions. It's in synaptic or you can install by running in terminal:

```
sudo apt-get install ntfsprogs
```

It's just my preference over ntfs-config.

As far as Magicjack, it's not yet supported in Linux. I never thought about using a virtual partition as described above.

A very nice "aid" to mounting most USB devices (such as flash drives) is pmount which is also in synaptic.

---

### Post by blandman3 on 2009-03-22
> **kansasnoob said:**
> If you install ntfsprogs you'll be able to access your ntfs partitions. It's in synaptic or you can install by running in terminal:

```
sudo apt-get install ntfsprogs
```

It's just my preference over ntfs-config.

As far as Magicjack, it's not yet supported in Linux. I never thought about using a virtual partition as described above.

A very nice "aid" to mounting most USB devices (such as flash drives) is pmount which is also in synaptic.

**Ok, I typed the code in, now what should I do?**

---

### Post by blandman3 on 2009-03-22
everytime i go to the places-->network and click on the windows network I get this message:

unable to mount location
-failed to retrieve share list from server

I have used the ntfs-config tool, but it only gives me an option to enable write support on external device, the internal device option is greyed out-unavailable.

I must have done something wrong, because my actual drive C:  which is hda2 is not being recognized.  Could this be that I also have ubuntu on the same drive?  I used "install inside windows" choice when I installed ubuntu.

---

### Post by blandman3 on 2009-03-22
HELP!!!

don't know why, but the damn thing will not let me access or mount anything!

---

### Post by kansasnoob on 2009-03-22
> **blandman3 said:**
> everytime i go to the places-->network and click on the windows network I get this message:

unable to mount location
-failed to retrieve share list from server

I have used the ntfs-config tool, but it only gives me an option to enable write support on external device, the internal device option is greyed out-unavailable.

I must have done something wrong, because my actual drive C:  which is hda2 is not being recognized.  Could this be that I also have ubuntu on the same drive?  I used "install inside windows" choice when I installed ubuntu.


Oh! This "I used "install inside windows" choice when I installed ubuntu." tells me I have no idea what to do!!!!!!!!!!!

That's a Wubi install (or it sounds that way), and I only tried Wubi briefly to see how it compared to an actual dual-boot. I prefer a dual-boot! But that won't help you with Magicjack, and I know almost nothing about Wubi!

So look here:

[http://www.wubi-installer.org/faq.php](http://www.wubi-installer.org/faq.php)

For instance:

> Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.


My biggest problem with Wubi is this:

> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


---

### Post by blandman3 on 2009-03-22
Thanks, I guess i didn't have to mount anything, because windows did that for me automatically.  I checked in my filesystem, and sure enough, it was there exactly under the file it said it would be under.

I was surely about to go out of my mind because every command was not working, but it makes sense now.

I appreciate everyone's help, I believe I have a fully functional ubuntu now, well.........except for my majicjack issue, lol!

---

### Post by blandman3 on 2009-03-22
Detect MagicJack USB devices:
I was initially having problem detecting the MagicJack USB devices. I did two things that fixed it:
1. Make sure the XP virtual machine has the USB Controller in the hardware list
2. Check that the vmx file of the virtual machine has:
usb.present = "TRUE"
usb.generic.skipsetconfig = "TRUE"
The second line is missing in my vmx file and I had to manually add it.

After this, I rebooted the guest XP OS and re-plug in the MagicJack. XP detected both devices properly and started its installation. After that the MagicJack is up and running and I was able to make calls.

**Where do I go to find/enter the vmx string so I can do this?**

---

