---
title: "mounting network drive in fstab Ubuntu 14.04"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by adam17 on 2014-04-21
Hi, 

I know this has probably been asked a hundred times but I am still unable to resolve my issue with mounting my server drive using the fstab.

I am running Ubuntu Server 12.04 and Ubuntu 14.04 Desktop while using nano to edit the fstab.

When mounting the network drive in the terminal I use the following: sudo mount //192.168.1.100/Disk\ 1 /media/Server
This works correctly and I can mount and umount to my hearts content.

However when entering into the fstab I run into trouble.

The file system of the drives are NTFS (I am not sure if that makes a difference)

I have tried adding to the FSTAB the following: //192.168.1.100/Disk\ 1 /media/Server cifs username=uname,password=pass 0 0

However it returns an error when using: sudo mount -a
[mntent]: line 14 in /etc/fstab is bad

What am I doing wrong I have seen on other sites that this has worked for people why not me?

Thanks

---

### Post by steeldriver on 2014-04-21
some answers in this thread --> [http://ubuntuforums.org/showthread.php?t=2218062](http://ubuntuforums.org/showthread.php?t=2218062)

---

### Post by adam17 on 2014-04-21
Thanks but I now get the following:
ntfs-3g: Failed to access volume '//192.168.1.100/Disk 1': No such file or directory

this is what I have in the fstab:
//192.168.1.100/Disk\0401        /media/Server  ntfs defaults 0 2

---

### Post by steeldriver on 2014-04-21
If it's a remote filesystem that you're accessing via CIFS, then specify the type as cifs - like you originally thought

```

//192.168.1.100/Disk\0401 /media/Server cifs username=uname,password=pass 0 0

```

---

### Post by adam17 on 2014-04-21
That got it. Thanks so much. Been scratching my head for hours on that one!

---

