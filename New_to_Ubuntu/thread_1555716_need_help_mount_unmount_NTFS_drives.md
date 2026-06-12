---
title: "need help mount unmount NTFS drives"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by henry cow on 2010-08-18
I am making great strides in understanding the file system / user system / permissions concepts here, after so many years in Microsoft world, but I am still thwarted. I have 3 Linux and Ubuntu books but none of them tell me how to do what I want in language that I can understand.

Somehow, I have fumbled around and gotten my 3 NTFS drives to mount automatically (one refuses to mount about 30% of the time) on boot-up, but without permissions to use them. I have an XP/10.04 dual-boot scenario with 3 large NTFS hard drives (single partition each) and another separate drive for Linux (in 3 partitions on an 80GB disk).

I need to clear them from the way I have them, and, for now, cause at least one of them ( /dev/sda1 -aka- C:\ ) to mount automatically on boot-up with full permission for me to read, create, delete, and write to it. I am the sole user of the computer. 

I would prefer to mount it into /home but seem to understand that is a problem, and that it would be better to mount it into /media. Whatever. The others ( /dev/sdb1 -aka- D:\ and /dev/sdd1 -aka- E:\ ) are big collections of mostly pictures and music and are not critical for everyday use.

If the permissions are not possible, I need for it to let me log in a password to do that, instead of simply telling me that access is denied with no recourse.

Am I dense or is this something difficult?

Thank you very much for your patience.

---

### Post by Morbius1 on 2010-08-18
> Somehow, I have fumbled around and gotten my 3 NTFS drives to mount  automatically (one refuses to mount about 30% of the time) on boot-up,  but without permissions to use them.Post the output of the following commands and it might be possible to just adjust what you've already done:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```

---

### Post by henry cow on 2010-08-18
Morbius - Thank you !


harry@harry-desktop:~$ sudo blkid -c /dev/null
[sudo] password for harry: 
/dev/sda1: UUID="AE486D70486D386B" TYPE="ntfs" 
/dev/sdb1: LABEL="HITACHI500GB" UUID="8020365220364F80" TYPE="ntfs" 
/dev/sdc1: UUID="0483c4e5-26a2-4da0-a6e1-e2b7a1289815" TYPE="ext4" 
/dev/sdc5: UUID="6a887208-f269-4abc-9444-657008d3b980" TYPE="swap" 
/dev/sdd1: LABEL="ST31500541AS" UUID="DA18929C1892776B" TYPE="ntfs" 


harry@harry-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sdc1    /    ext4    errors=remount-ro    0    1
/dev/sdb1    /media/HITACHI500GB    ntfs-3g    defaults,locale=en_US.UTF-8    00
/dev/sdd1    /media/ST31500541AS    ntfs    defaults,nls=utf8,umask=0222    00
/dev/sda1    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sdc5    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0


sda1 is the one that is most important to me. I really would like to have full permissions on it all the time, automatically if possible. I would like to have "C:\....My Documents" as easily accessible as possible, ideally I would want a mount point to be something like /home/NTFS-C

is that asking too much?

sdb1 and sdd1 are data disks and I do not access them a lot, but would like to have them available. I would be happy to take them off automatic and mount them when I want to use them.

also, sdc1 causes an error from time to time on boot-up, and I have to "S" skip mounting it or the whole system hangs. these are all fairly new hard drives in excellent condition, so I am not inclined to think that it is nearing failure.

thank you for your help

---

### Post by mapes12 on 2010-08-18
You could try changing permissions with nautilus launched with sudo permissions: ```
gksudo nautilus
```then navigate to the device on which you want to change permissions. Right click it>Properties then select the Permissions tab. Make the changes in the GUI then close Nautilus and Terminal.

If you have Nautilus open as above and you want to delete anything make sure you press the shift key at the same time as pressing delete. Otherwise you will end up filling Roots trash bin without knowing it and then wonder where your disk space has gone.

---

### Post by Morbius1 on 2010-08-18
From blkid:
> /dev/sda1: UUID="AE486D70486D386B" TYPE="ntfs" 
/dev/sdb1: LABEL="HITACHI500GB" UUID="8020365220364F80" TYPE="ntfs" 
/dev/sdd1: LABEL="ST31500541AS" UUID="DA18929C1892776B" TYPE="ntfs" From fstab:
> /dev/sda1    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sdb1    /media/HITACHI500GB    ntfs-3g    defaults,locale=en_US.UTF-8    00
/dev/sdd1    /media/ST31500541AS    ntfs    defaults,nls=utf8,umask=0222    00What's curious about all this is that should work. I wouldn't have written the lines like that myself but the only mistakes are the ending "00" at the end of sdb1 and sdd1. It should be "0 0" - a space between the zeros.

All of those ntfs lines should have produced a mount point owned by root but with read / write access to everyone. Except sdd1 which has write turned off.

Let's try this:
Make a new mount point for sda1:
```
sudo mkdir /home/NTFS-C
```Edit fstab as root:
```
gksu gedit /etc/fstab
```Change this line:
> /dev/sda1 [COLOR=Blue]   /media/sda1[/COLOR]    ntfs-3g    defaults,locale=en_US.UTF-8    0    0to this:
> /dev/sda1 [COLOR=Blue]/home/NTFS-C[/COLOR]    ntfs-3g    defaults,locale=en_US.UTF-8    0    0Save the file and then just to make sure there is no interference from anything else run these two:
```
sudo umount /media/sda1
``````
sudo mount -a
```Report any errors you may get after the "mount -a" command and see if you can access /home/NTFS-C ( no need to reboot )

> then navigate to the device on which you want to change permissions.  Right click it>Properties then select the Permissions tab. Make the  changes in the GUI then close Nautilus and Terminal.Linux can't change ownership or permissions on a windows filesystem. That can only be done with a mount or in fstab.

---

### Post by henry cow on 2010-08-18
Thanks, Morbius.

I think this worked, and I seem to be able to open, change, and save a document to my NTFS device in Open Office now, at least. 

I have the drives shown on my desktop as icons, which is OK, but I would remove the last 2 since they are in /home now and easily accessible. The last one still shows a lock on its icon, which is not bad, but I will need to modify it one day.

This is all confusing to me still. I thought that I did my original operation with a wizard instead of at the command line, but may be wrong. 

You were very helpful. Thank you.

---

### Post by Morbius1 on 2010-08-19
It's still not clear to me why these didn't work ( except for the "00" at the end of sdb1 and sdd1 ):
> /dev/sda1    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sdb1    /media/HITACHI500GB    ntfs-3g    defaults,locale=en_US.UTF-8    00
/dev/sdd1    /media/ST31500541AS    ntfs    defaults,nls=utf8,umask=0222    00                      If you had no entries in fstab for those partitions the system would have created temporary mount points at those exact same locations. Had you run the utility after you temporarily mounted them then the utility would have tried to create a permanent mount point but failed - silently.

Anyway, that was the theory I was working under when I suggested you create a permanent mount point completely outside of /media so there would never be a conflict. 
> I have the drives shown on my desktop as icons, which is OK, but I would  remove the last 2 since they are in /home now and easily accessible.  The last one still shows a lock on its icon, which is not bad, but I  will need to modify it one day.If you've created links to the mount points on your desktop , they should all have locks on them because you're linking to a folder that you do not own - root owns them. It really doesn't matter though because you should have full read / write access to them anyway.

If the locks bother you there is a way to remove them and that's to take possession of the mount point.
For sda1, for example, you would change this:
>                               /dev/sda1 [COLOR=Black]/home/NTFS-C[/COLOR]    ntfs-3g    defaults,locale=en_US.UTF-8    0    0                      To this:
>  /dev/sda1 [COLOR=Black]/home/NTFS-C[/COLOR]    ntfs-3g    defaults,[COLOR=Blue]uid=1000[/COLOR],locale=en_US.UTF-8    0    0uid=1000 is the user id and 1000 should be you. To make sure 1000 is you open a terminal and type:
```
id
```All of these utilities and wizards tend to produce unintended results and I think they should all be purged from the repositories - but I'm kind of old school when it comes to this sort of thing. ;)

---

