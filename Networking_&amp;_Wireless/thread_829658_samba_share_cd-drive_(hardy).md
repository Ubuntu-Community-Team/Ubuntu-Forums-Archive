---
title: "samba share cd-drive (hardy)"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by fredknex on 2008-06-15
How can i share my cd/dvd-rom drive over my samba network?  The drive is on an Ubuntu 8.04 Hardy machine.  I have already set up samba and successfully shared my external drive over the network, but do not know what directory to set the share as in samba.
When i insert a disk, it is mounted in /media/"discname" which i am able to share.  However this is semi useless as it only works for discs of whatever name i set it to.  

**Is there any way to share whatever disk is in the drive automatically?** 

much thanks for any possible help




(smb.conf mentions editing fstab. the default examples given do not seem to work)

---

### Post by kaleo86 on 2008-06-24
As you know, in UNIX Systems, Hard Drives are mapped and used as a part of the file directory, such as /dev/cdrom mapped to /media/cdrom etc...

If you want to share a hard drive, you just need to share the directory where the drive is mapped (in the case before, /media/cdrom) ...

try editing the samba's config file as:

```
sudo gedit /etc/samba/smb.conf
```

then, chance the follow section as:

```

[public]
   comment = Public Stuff
   path = /dir where your drive is mapped
   public = yes
   writable = yes
   printable = no
```


I hope this can help you...

---

### Post by kaleo86 on 2008-06-24
See this:

[http://oreilly.com/catalog/samba/chapter/book/ch04_01.html]("http://oreilly.com/catalog/samba/chapter/book/ch04_01.html")

---

### Post by fredknex on 2008-06-25
Thanks for the info, from what i've been reading my problem is most likely fstab, since i can share the cd drive manually but not automatically, if that makes sense

---

### Post by dmizer on 2008-06-25
> **kaleo86 said:**
> As you know, in UNIX Systems, Hard Drives are mapped and used as a part of the file directory, such as /dev/cdrom mapped to /media/cdrom etc...

If you want to share a hard drive, you just need to share the directory where the drive is mapped (in the case before, /media/cdrom) ...

try editing the samba's config file as:

```
sudo gedit /etc/samba/smb.conf
```

then, chance the follow section as:

```

[public]
   comment = Public Stuff
   path = /dir where your drive is mapped
   public = yes
   writable = yes
   printable = no
```


I hope this can help you...

actually, since it's a dvd ROM, it should look like this:
```
[DVD-ROM Drive]
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = yes
```
usually the dvd is mounted at /media/cdrom and then a symbolic link is created so that you will see the dvd as a name on your desktop.  if you have more than one cd/dvd drive, this could be /media/cdrom1

---

