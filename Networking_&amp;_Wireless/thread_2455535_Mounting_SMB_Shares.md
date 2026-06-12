---
title: "Mounting SMB Shares"
date: 2020-12-21
forum: Networking &amp; Wireless
---

### Post by mav06 on 2020-12-21
Good Evening! 

I am a new Linux user and have been struggling a bit. I have purchased a HP 290 for my Plex Server and have installed Ubuntu Desktop 20.04 on the machine. I am struggling with mounting my windows 10 shared drive (Currently where all my Media is stored). Currently I am just trying to get the drive to mount to see if it works and then will edit the /mnt /fstab file so it will mount automatically. The idea is to try and mount the whole drive so I have access to all of the folders on there for Plex. To test I have tried the following command
 
sudo mount -t cifs //192.168.1.178/j /mnt/Plex ( It then asks for a password which I put in)
 
I get this error:
mount error(13): Permission denied
 
When I check the Kern.log I have the following error:
 
Dec 21 15:41:54 Plex-Server kernel: [ 2113.303927] CIFS VFS: cifs_mount failed w/return code = -13
 
Also I have went head and tried to edit the /etc/fstab file with the following:
 
//192.168.1.178/j /mnt/Plex ntfs,username=“Media Server”,password=XXXXXXX,iocharset=utf8,sec=ntlm defaults,noatime,nofail 0 0
 
I then do sudo mount -a and get this:
 
mount: /etc/fstab: parse error at line 13 – ignored
 
I know i must be missing something very simple in all of this, any help would be greatly appreciated.

---

### Post by deadflowr on 2020-12-21
> Also I have went head and tried to edit the /etc/fstab file with the following:

//192.168.1.178/j /mnt/Plex ntfs,username=“Media Server”,password=XXXXXXX,iocharset=utf8,sec=ntlm defaults,noatime,nofail 0 0

I then do sudo mount -a and get this:

mount: /etc/fstab: parse error at line 13 – ignored

Should be a space between ntfs and username as one is one thing and the other is another thing.
The way it shows is they are all options, which ntfs is not.
Also everything after ntfs and before the first 0 is an option
so it should go from this
```
//192.168.1.178/j /mnt/Plex **ntfs,username**=“Media Server”,password=XXXXXXX,iocharset=utf8,sec=**ntlm defaults**,noatime,nofail 0 0

```
To this
```
//192.168.1.178/j /mnt/Plex **ntfs username**=“Media Server”,password=XXXXXXX,iocharset=utf8,sec=**ntlm,defaults**,noatime,nofail 0 0

```

Beyond that I cannot help.
Though it seems the error 13 mount issue might be security option related.
See: [https://unix.stackexchange.com/questions/124342/mount-error-13-permission-denied]("https://unix.stackexchange.com/questions/124342/mount-error-13-permission-denied")
for possible solutions to that.

---

