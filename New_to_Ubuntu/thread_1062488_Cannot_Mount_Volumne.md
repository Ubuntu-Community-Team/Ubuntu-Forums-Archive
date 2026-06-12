---
title: "Cannot Mount Volumne"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Jim Rimedio on 2009-02-06
When I attempted to mount a WD PassPort USB flash drive I received the following message: Cannot mount volume - Unable to mount the volum 'WD Passport 2009.2.5' - Details $LogFile indicates unclean shutdown (0.0) Filed to mount '/dev/sdc1": Operation not supported Mount is denied because NTFS is marked to be in use.  Chose one action: Choice 1: if you have Windows then disconnect the external devices by clicking on 'Safely Remove Hardward' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: if you don't have Windows then you can use the 'forced' option for your own responsibility. For example they on the command line: mount-t ntfs-3g /dev/sdc1 /media/WD Passport 2009.2.5 -o force Or add the option to the relevant row in the /etc/fstab file: sdc1 /media/WE Passport 2009.2.5 ntfs-3g force 00

When I tried to mount via computer I received the following:

Unable to mount location - DBus error ord.freedesktopp DBus Error NoReply. Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blockedthe reply, the reply timeout expired, or the network connection was broken.

I check Ubuntu Help for mounting UBS devies and located  [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

In went to System->Preferences->Removable Drives and Media which did not contain any information about a UBS flash drive.

Upon further research I suspect I disconnected the device and neglected to unmount it first.

I am new to Linux and Ubuntu.  I check  man mount (8) but frankly the instructions are beyond my knowledge and skill level.

Then I tired 

jim@jim-desktop:~$ sudo fdisk -l 
sudo: unable to resolve host jim-desktop 
[sudo] password for jim: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes 
255 heads, 63 sectors/track, 4865 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x843e3ca7 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        4678    37576003+  83  Linux 
/dev/sda2            4679        4865     1502077+   5  Extended 
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris 

Disk /dev/sdb: 40.0 GB, 40020664320 bytes 
255 heads, 63 sectors/track, 4865 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x3df2277d 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1        3479    27945036    7  HPFS/NTFS 

Disk /dev/sdc: 60.0 GB, 60011642880 bytes 
255 heads, 63 sectors/track, 7296 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x28f12a69 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1        7295    58597056    7  HPFS/NTFS 
jim@jim-desktop:~$ 

 tired sudo mount -t ntfs-3g /dev/sdb1 /media/external and received the following:

jim@jim-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137 
sudo: unable to resolve host jim-desktop 
mount: /dev/sdb1 already mounted or /media/external busy 
mount: according to mtab, /dev/sdb1 is mounted on /media/Backup2_ 
jim@jim-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/external 
sudo: unable to resolve host jim-desktop 
jim@jim-desktop:~$ 

I then tried:
jim@jim-desktop:~$ lsusb 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 1058:0701 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
jim@jim-desktop:~$ 

lauI am converting from Microsoft to Linus running Ubuntu and the data on the USB drive contains critical information that I need in Documents.

If I corrupted the file system, is there a fix other than reformatting the hard drive and starting over?
The box does not have any other operating system installed, just Linux running Ubuntu.

Now I am hopelessly lost

---

### Post by taurus on 2009-02-06
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdc1
sudo mkdir /media/sdc1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
df -h
```

And try to unmount it first when you are done before you unplug it.

```
sudo umount /media/sdc1
```

---

