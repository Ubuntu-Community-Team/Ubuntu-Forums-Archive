---
title: "can't backup to network hard drive"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by SLUHjrbill12 on 2009-05-03
i can't find a backup program that will let me backup my system to a wireless hard drive. i access the hard drive by typing smb://"ipaddress". should i be doing something differently to mount the drive that will allow me to back up to it. i'm looking for a program with a gui.

---

### Post by cariboo on 2009-05-03
I personally use grsync to backup my home directory to my file server. Grsync is available in the repositories. For other backup programs go to System-->Administration-->Synaptic Package Manager, click the search button and type backup.

---

### Post by SLUHjrbill12 on 2009-05-03
how can i select my network hard drive as the destination? in the file browser it appears as "username" on "ipaddress" but in grsync (or any other backup program for that matter) it's not an option or it show up as a drive but it can't be mounted

---

### Post by rhcm123 on 2009-05-03
> **SLUHjrbill12 said:**
> how can i select my network hard drive as the destination? in the file browser it appears as "username" on "ipaddress" but in grsync (or any other backup program for that matter) it's not an option or it show up as a drive but it can't be mounted

the drive must be mounted locally, in the /etc/fstab, for programs to properly use the network drive.

run the following command:
```
sudo nano /etc/fstab
```

then add this line at the bottom of the file:
```
//IP.ADDRESS/SHARE-NAME /media/MAKE A DIRECTORY FOR A MOUNTPOINT smbfs credentials=/home/YOURUSERNAME/.smb1,umask=777 0 0
```

Use ctrl-x to writeout and exit. then run this command:
```
nano /home/YOURUSERNAME/.smb1
```

write the following lines into that file:
```
username=USERNAME FOR THE SERVER
password=PASSWORD FOR SAID USERNAME

```

Yes, i know that stores your password in cleartext, but it is better than storing it in the all-user-readable fstab, right?! Make it readable only to you with this command:
```
sudo chmod 400 /home/YOURUSERNAME/.smb1 && sudo chown YOURUSERNAME /home/YOURUSERNAME/.smb1
```

then run this command to mount the share:
```
sudo mount -a
```

This should get your share working properly

---

### Post by SLUHjrbill12 on 2009-05-03
after entering sudo mount -a i get:

 [mntent]: line 1 in /etc/fstab is bad
mount: special device /dev/disk/by-uuid/E0FD-1813 does not exist
mount error: can not change directory into mount target /media/NetworkDrive

---

### Post by rhcm123 on 2009-05-03
> **SLUHjrbill12 said:**
> after entering sudo mount -a i get:

 [mntent]: line 1 in /etc/fstab is bad
mount: special device /dev/disk/by-uuid/E0FD-1813 does not exist
mount error: can not change directory into mount target /media/NetworkDrive

Alright, this indicates three problems:
1. I don't know why the first line of the fstab is bad - probably some garbage charecters. post your fstab, ill see if i can clean it up.

2. The first mount error (special device) indicates you have some drive that is not responding. This is typically a usb drive. You can probably ignore this.

3. The last one (cant change directory) is fairly simple. The mount point dosent exist. Fix that with this command:
```
sudo mkdir /media/NetworkDrive
```
then run sudo mount -a to mount the drive

---

### Post by rhcm123 on 2009-05-03
Also, one thing that i forgot. This (mounting a network drive in the fstab) may slow down your shudowns, but you can fix that with this command:
```
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
&& sudo ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```

---

### Post by SLUHjrbill12 on 2009-05-03
my fstab:

```
0# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sda5 :
UUID=8171c526-873c-47a3-896d-6d954d8b12b3       /       ext3    relatime,errors=remount-ro      0       1
#Entry for /dev/mmcblk1p1 :
UUID=E0FD-1813  /media/disk     vfat    defaults,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0       2
#Entry for /dev/sda1 :
UUID=2501DF733CF40735   /media/windows  ntfs-3g defaults,auto,locale=en_US.UTF-8        0       0
#Entry for /dev/sda6 :
UUID=bb616040-6774-43e1-86f3-eb5a8a3bdcbc       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8   0       0
//IPADDRESS/USERNAME        /media/NetworkDrive     smbfs credentials=/home/USERNAME/.smb1,umask=777        0       0
```




i changed my ip address and username but you get the point

---

### Post by rhcm123 on 2009-05-03
> **SLUHjrbill12 said:**
> my fstab:

```
0# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sda5 :
UUID=8171c526-873c-47a3-896d-6d954d8b12b3       /       ext3    relatime,errors=remount-ro      0       1
#Entry for /dev/mmcblk1p1 :
UUID=E0FD-1813  /media/disk     vfat    defaults,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0       2
#Entry for /dev/sda1 :
UUID=2501DF733CF40735   /media/windows  ntfs-3g defaults,auto,locale=en_US.UTF-8        0       0
#Entry for /dev/sda6 :
UUID=bb616040-6774-43e1-86f3-eb5a8a3bdcbc       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8   0       0
//IPADDRESS/USERNAME        /media/NetworkDrive     smbfs credentials=/home/USERNAME/.smb1,umask=777        0       0
```




i changed my ip address and username but you get the point
Im assuming that you made the mount point with the mkdir command i gave you?

Also, I've spotted the problem. At the begining of the file it says "0# /etc/fstab...". Delete the 0 and it should stop complaning.

I think this is about all you'll need - from the fstab, the "UUID=E0FD-1813" drive you were having problems with is a usb drive... (although correct me if I'm wrong) :)

---

### Post by SLUHjrbill12 on 2009-05-03
i deleted the zero but i still get

```
mount: special device /dev/disk/by-uuid/E0FD-1813 does not exist
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```


i have no idea what the "UUID=E0FD-1813" drive is from. i dont even have a usb drive plugged in though i did have trouble mounting a usb drive once as well as an sd card if that could have changed anything

---

### Post by rhcm123 on 2009-05-03
> **SLUHjrbill12 said:**
> i deleted the zero but i still get

```
mount: special device /dev/disk/by-uuid/E0FD-1813 does not exist
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```


i have no idea what the "UUID=E0FD-1813" drive is from. i dont even have a usb drive plugged in though i did have trouble mounting a usb drive once as well as an sd card if that could have changed anything

Then i have no idea what that device is, but from the fstab it looks like it was a fat32 drive connected to your pc at boot and mounted to /media/disk (the default mount point for usb drives).

Mount error 13 means that you have the wrong credentials (i.e. password). Are you sure you are using sudo mount -a to mount?

Also, if your server is IP 192.168.2.190, and on that server you have this setup in your smb.conf:
```

[drives]
path=/blah, this is an example
```

then this should be the line in the /etc/fstab:
```
//192.168.2.193/drives
```

---

