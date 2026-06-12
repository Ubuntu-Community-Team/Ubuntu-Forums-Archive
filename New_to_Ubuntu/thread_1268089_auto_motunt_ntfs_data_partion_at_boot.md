---
title: "auto motunt ntfs data partion at boot"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by poliltimmy on 2009-09-16
IU am totally confused on how to set up my data partition to mount at boot. Could someone help me please?

timmy@timmy-pawpawsliltoy:~$ sudo blkid
/dev/sda1: UUID="52A4D570A4D55757" LABEL="Data" TYPE="ntfs" 
/dev/sda2: UUID="D69078B590789DA5" TYPE="ntfs" 
/dev/sda5: UUID="c77c4698-8c3d-4063-80d0-9a3f323d15aa" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="8c51cb21-ac16-403e-aed1-5c2bf3365310" 

The first entry is my ntfs data partition. Thanks in advance.

---

### Post by sisco311 on 2009-09-16
Edit the fstab file:
```
gksu gedit /etc/fstab
```

And add this line at the end of the file:
```
UUID=52A4D570A4D55757 /media/data ntfs defaults,nls=utf8,umask=007,gid=46 0 2
```

Create the mount point:
```
sudo mkdir /media/data
```

Make sure that your user is in the plugdev group:
```
sudo gpasswd -a $USER plugdev
```

Mount the partition:
```
sudo mount -a
```

---

### Post by bryceowen on 2009-09-16
Dammit, Sisco...  I wanted to help for once... Here I had written everything out and you had to snipe a reply while I was previewing my post.

You are now my ARCH NEMESIS!!  *DUN**DUN**DUNNNNNNN*

Or not. I just gotta type faster. ;)

---

### Post by rustutzman on 2009-09-16
You will need to edit /etc/fstab and use the uuid from above. Create a directory in /media with the name you want the drive mounted under. I used Data in the example below. If you create /media/Data you should be able to cut and paste the line below into your fstab. Be sure to make a backup copy before doing any editing.

```

gksudo gedit /etc/fstab

```

```

# Entry for /dev/sda1:
UUID=52A4D570A4D55757/media/Data ntfs-3g  umask=000 0 0

```

Russ

---

### Post by poliltimmy on 2009-09-16
I did what sisco311 said to do and it mounted on reboot. Do I have to do what rustutzman has suggested also?

and also am I to add all of it as followed including #:

# Entry for /dev/sda1:
UUID=52A4D570A4D55757/media/Data ntfs-3g  umask=000 0 0

---

### Post by sisco311 on 2009-09-16
> **poliltimmy said:**
> I did what sisco311 said to do and it mounted on reboot. Do I have to do what rustutzman has suggested also?

No, you don't. If everything works, then please mark this thread as solved.

---

### Post by poliltimmy on 2009-09-16
Thanks a bunch!!!!                        :guitar:

---

