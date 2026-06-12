---
title: "cannot mount secondary harddrive"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by rudedcam on 2006-12-04
the harddrive is set up allright, in fact, my secondary harddrive used to be mounted at all time... used to work ;)

when i try to mount it it gives me this message.

> erreur : le périphérique /dev/hdb5 n'est pas amovible

erreur: impossible d'exécuter pmount

which means literaly:
error: the peripheral /dev/hdb5 is not removable
error: impossible to execute pmount

anyone can help me out?

thanks guys 
rudecam

---

### Post by fervilla on 2006-12-04
Have you been mounted this partition before from linux?
What ubuntu version do you have?
Can you put the mount command?

My ubuntu version (6.10) mount all automatically.

---

### Post by rudedcam on 2006-12-05
the harddrive has only one partition in "fat32" (spelling) originally set up with windows XP but it was then mounted with linux (ubuntu).

i have Ubuntu 6.06 LTS - Dapper Drake

when i try to mount (right click or double click) that's when it gives me the error message. I don't know the terminal commands to mount... eh! what can i say...

note: prior to that, it was automatically mounted upon start up... one day it didn't and that's where i stand today!;)

thanks for taking your time fervilla.

the cam :)

---

### Post by bulldog on 2006-12-08
Can you give me the output of```
sudo fdisk -l (l as in like)
```

Here you can find all you have to know about mounting your drive in fstab,

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

If you try to mount it in a directory in /mnt you should be able to mount.
```
sudo mkdir /mnt/windows
```
```
sudo mnt vfat /dev/hdb5 /mnt/windows
```
This should do it for manually mounting.
To mount automatically you have to add a line in your fstab,which you can find in the link I provided.

Another one which is very informative,

[http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572](http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572)

**off topic**
You should get a better response if you post your question in the right thread.
Networking & Wireless isn't the place to get help for a mounting problem.

---

### Post by rudedcam on 2006-12-10
all right sorry for taking so long, took me a while to digest all that. here's the outcome of it:

```
rudecam@Ganesh:~$ sudo fdisk -l
Password:

Disque /dev/hda: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1               1        1044     8385898+  83  Linux
/dev/hda2            1045        1305     2096482+  82  Linux swap / Solaris
/dev/hda3            1306        9729    67665780   83  Linux

Disque /dev/hdb: 120.0 Go, 120060444672 octets
240 têtes, 63 secteurs/piste, 15508 cylindres
Unités = cylindres de 15120 * 512 = 7741440 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1               2       15508   117232920    f  W95 Etendu (LBA)
/dev/hdb5               2       15508   117232888+   b  W95 FAT32
rudecam@Ganesh:~$ sudo mkdir /mnt/windows
mkdir: Ne peut créer le répertoire `/mnt/windows': Le fichier existe.
rudecam@Ganesh:~$ sudo mnt vfat /dev/hdb5 /mnt/windows
sudo: mnt: command not found
rudecam@Ganesh:~$

```

note:
the line where it sais : "rudecam@Ganesh:~$ sudo mkdir /mnt/windows" the outcome of that sais that it cannot create the folder 'cause i already created it" (i have the french version:P)

I also tried other an way that was given in one the link you gave me without sucess. plus i'm not sure to understand fully the roll of "fstab"

feels like a blind man trying to swim to shore!](*,)

cam :D

**off topic**
i created a new thread (not finding how to move it) in "Hardware & Laptops" 
[http://ubuntuforums.org/showthread.php?p=1868872#post1868872]("http://ubuntuforums.org/showthread.php?p=1868872#post1868872")

---

### Post by taurus on 2006-12-10
I just answered your post in Hardware & Laptops so I will remove that one then.

Paste the output of your /etc/fstab here...

```
cat /etc/fstab
```

---

### Post by rudedcam on 2006-12-10
```
rudecam@Ganesh:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
#/dev/hdb5      /media/Storage  vfat    users           0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
rudecam@Ganesh:~$

```

---

### Post by taurus on 2006-12-10
```

/dev/hdb5   /media/Storage  vfat   iocharset=utf8,umask=000  0  0

```

---

### Post by rudedcam on 2006-12-10
it works! thanks taurus! appreciate your help:KS

with your help and after seeing that link... [http://psychocats.net/ubuntu/mountlinux]("http://psychocats.net/ubuntu/mountlinux")
i did:
```
rudecam@Ganesh:~$ sudo pico /etc/fstab
rudecam@Ganesh:~$ sudo mount -a
rudecam@Ganesh:~$ 

```

that brings me to my next question; how can i change the rights of a folder and all that is under it?
here's what i did 
```
rudecam@Ganesh:/media/Storage$ sudo chmod 777 junk/

```
but lots of sub-folder of "junk/ still dont have all the permissions! i think it as to do with a "-r"... tried to place it everywhere in the line above and... failed! lol

anybody's got the right line? 


thank you all for helping the newbie!

**off topic**
ubuntu is a lot of fun! at least it makes sense! ain't like "macrosoft windows" lol:p

---

