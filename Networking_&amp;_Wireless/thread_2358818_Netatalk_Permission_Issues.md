---
title: "Netatalk Permission Issues"
date: 2017-04-17
forum: Networking &amp; Wireless
---

### Post by jasonamri on 2017-04-17
Hi,

I've been having issues with Netatalk related to permissions.

**Background:**
I am currently running Lubuntu 16.04 on an iBook G3 with 256mb of RAM. So far I haven't had any problems with the machine's low specs. It has a wired connection into our wireless router.

I have a WD 1tb drive partitioned into 4 parts all with a Fat32 (vfat) filesystem. They are called "TimeMachine", "HomaBackup", "MoviesTV", "JasonDrive" and are mounted at /TimeMachine, /HomaBackup, etc.

*sudo fdisk -l* returns:
```
**Device**     **Boot** **    Start** **      End** ** Sectors** ** Size** **Id** **Type**
/dev/sdb1  *          2048  699045887 699043840 333.3G  b W95 FAT32
/dev/sdb2        699045888 1398089727 699043840 333.3G  b W95 FAT32
/dev/sdb3       1398089728 1922377727 524288000   250G  b W95 FAT32
/dev/sdb4       1922377728 1953519615  31141888  14.9G  b W95 FAT32
```

*/etc/fstab file:*
```
#NAS server partitions
#Time Machine
/dev/sdb1 /TimeMachine vfat defaults 0 2


#Homas backup
/dev/sdb2 /HomaBackup vfat defaults 0 2


#Movies and TV
/dev/sdb3 /MoviesTV vfat defaults 0 2


#Jasons drive
/dev/sdb4 /JasonDrive vfat defaults 0 2
```


I have two users setup to access the drives: *homa* and *jason.*

I also currently have a samba server running on this machine. When I access the samba shares on a Mac (OSx 10.12.3, Sierra) or a PC (Windows 10), there are no issues. 

*/etc/samba/smb.conf*
```
[HomaBackup]
   comment = Homa's Backups
   path = /HomaBackup
   browsable = yes
   read only = no
   guest ok = no
   valid users = homa jason
   create mask = 0777
   directory mask = 0777




[MoviesTV]
   comment = Movies and TV Shows
   path = /MoviesTV
   browsable = yes
   read only = no
   guest ok = yes
   valid users = homa jason
   create mask = 0777
   directory mask = 0777


[JasonDrive]
   comment = Jason's Drive
   path = /JasonDrive
   browsable = yes
   read only = no
   guest ok = no
   valid users = jason
   create mask = 0777
   directory mask = 0777

```

I am trying to also setup the same shares with AFP and Netatalk. I am running Netatalk 3.1.11. My afp.conf file is below.

[I]/usr/local/etc/afp.conf:
[/I]```
[Global]
; Global server settings
   spotlight = yes
   save password = no


; [Homes]
; basedir regex = /xxxx


; [My AFP Volume]
; path = /path/to/volume


; [My Time Machine Volume]
; path = /path/to/backup
; time machine = yes




[TimeMachine]
   path = /TimeMachine
   time machine = yes
   spotlight = no
   valid users = jason
   file perm = 777
   umask = 777
   directory perm = 777
   file perm = 777
[HomaBackup]
   path = /HomaBackup
   time machine = no
   spotlight = yes
   valid users = jason
   file perm = 777
   umask = 777
   directory perm = 777
   file perm = 777


[MoviesTV]
   path = /MoviesTV
   time machine = no
   spotlight = yes
   valid users = jason
   file perm = 777
   umask = 777
   directory perm = 777
   file perm = 777


[JasonDrive]
   path = /JasonDrive
   time machine = no
   spotlight = yes
   valid users = jason
   file perm = 777
   umask = 777
   directory perm = 777
   file perm = 777

```

If it makes a difference, I also have an OpenSSH server and a Transmission web interface running.


**Problem:**
Netatalk and Avahi are running fine and I can see all of shares in Finder, and I can connect fine.

When I (logged in as user *jason)* try to create a folder I get this error message:
[IMG]http://i.imgur.com/n1AqYTu.png[/IMG]

I have also gotten error -8085.

I also cannot create Time Machine backups to the TimeMachine folder.

Any help is greatly appreciated. Please let me know if any other conf or log files would shed more light on this issue.

---

