---
title: "Can Mount Network Shares using GUI, but not Command Line"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by mojohn on 2008-11-24
I'm running Intrepid on a desktop and Hardy on a laptop.

Both machines are able to mount a USB hard drive attached to my wife's WinXP machine using Nautilus, but when I try to mount the drive using the command line [sudo mount -t cifs //office/backup /mnt/windows] or sudo mount -a [after amending fstab by adding the following line - //office/backup /media/backup cifs guest,rw,file_mode=0777,dir_mode=0777 0 0], I get the following error message on both machines: 

[INDENT]mount error 6 = No such device or address[/INDENT]

I've tried using both the netBIOS name for the share and the url of the WinXP machine. 

I followed the directions at [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534), but for some reason I am unable to mount using the CLI or fstab. 

Any suggestions?

Thanks, mojohn

---

### Post by mojohn on 2008-12-15
Bump, please?

---

### Post by bab1 on 2008-12-15
> Both machines are able to mount a USB hard drive attached to my wife's WinXP machine using Nautilus, but when I try to mount the drive using the command line...

The reason this occurs is due to the differing underlying routines (libs) used.  I believe you need to add the smbclient and samba-common packages for fstab to work properly.

The real question is; why mount the shares via fstab?.  Particularly if it is a transient connection like an external USB connected HDD.I have 4  samba shares and none are mounted via fstab.  They are bookmarked though.  This seems to be enough for all my users needs.

---

