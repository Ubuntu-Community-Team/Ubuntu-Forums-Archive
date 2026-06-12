---
title: "How Can I Mount My Disk - Space Character in Folder"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by mulluysavage on 2009-12-14
For a long time i had my usb HD mounted at a /media/My Book

All of my songbird files are cataloged here. I'm trying to re-connect my disk with my songbird database.

Right now my disk won't mount: when i mount -a error= line is bad.

When I try to mount to a directory /media/MyBook it works. So I figure it's the space.

in fstab, an entry with /media/My\ Book doesn't work either.

help!

---

### Post by philinux on 2009-12-14
> **mulluysavage said:**
> For a long time i had my usb HD mounted at a /media/My Book

All of my songbird files are cataloged here. I'm trying to re-connect my disk with my songbird database.

Right now my disk won't mount: when i mount -a error= line is bad.

When I try to mount to a directory /media/MyBook it works. So I figure it's the space.

in fstab, an entry with /media/My\ Book doesn't work either.

help!

snip

---

### Post by mulluysavage on 2009-12-14
> **philinux said:**
> snip

excuse me?

---

### Post by philinux on 2009-12-14
> **mulluysavage said:**
> excuse me?

Forum etiquette. I posted the wrong thing hence snipped it out. 

After looking at this I would get rid of the space using Sys>admin>disk utility.

---

### Post by lotharmat on 2009-12-14
Does enclosing the path in quotes work?

---

### Post by ukripper on 2009-12-14
> **mulluysavage said:**
> 

When I try to mount to a directory /media/MyBook it works. So I figure it's the space.

in fstab, an entry with /media/My\ Book doesn't work either.

help!

What is wrong in creating MyBook instead of My Book? you still access the same files from the same drive. It is not like My Book will add anything extra.:confused:

---

### Post by mulluysavage on 2009-12-14
> **ukripper said:**
> What is wrong in creating MyBook instead of My Book? you still access the same files from the same drive. It is not like My Book will add anything extra.:confused:

all my entries in my songbird database are already pointed to My Book so I want to have it named that way

---

### Post by ukripper on 2009-12-14
ok in that case let's see. Can you run these commands post output here:

this will unmount already mount My Book
```
sudo umount /media/My\ Book
```
this will mount all fstab entries. post output of this:
```
sudo mount -a
```
post output of this:
```
gedit /etc/fstab
```

---

### Post by John Bean on 2009-12-14
In /etc/fstab try using the character sequence "%20" (without the quotes) to replace the embedded space in "My Book" - so it becomes "My%20Book" with no spaces.

Edit: ... or should it be octal, ie "%040"? Hm, maybe I should test before posting next time. Anyhow, one of them might work... perhaps ;-)

---

### Post by mulluysavage on 2009-12-14
> **ukripper said:**
> ok in that case let's see. Can you run these commands post output here:

this will unmount already mount My Book
```
sudo umount /media/My\ Book
```


this will mount all fstab entries. post output of this:
```
sudo mount -a
```
post output of this:
```
gedit /etc/fstab
```

umount /media/My\ Book: not mounted

sudo mount -a
[mntent]: line 13 in  /etc/fstab is bad

gedit /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=48965a9d-2363-4aee-896c-72e4c6ebb054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1	/media/60GBclone	vfat	rw	0	0
/dev/sda6	/media/sriracha		ext3	defaults	0	0
UUID=0380-924F 	/media/My Book		vfat 	rw 	0 	0

---

### Post by mulluysavage on 2009-12-14
> **John Bean said:**
> In /etc/fstab try using the character sequence "%20" (without the quotes) to replace the embedded space in "My Book" - so it becomes "My%20Book" with no spaces.

mount point /media/My%20Book does not exist

(there is in fact a mount point "My Book" in /media)

---

### Post by mulluysavage on 2009-12-14
> **lotharmat said:**
> Does enclosing the path in quotes work?

[mntent]: line 13 in /etc/fstab is bad

---

### Post by sisco311 on 2009-12-14
```
UUID=0380-924F /media/My**\040**Book vfat rw 0 0
```


[noparse]
\040 - is an escape sequence. 040 is the ascii code, in octal(base 8) number system, of the space. The mount command interprets \040 as literal space in the mount point.[/noparse]

---

### Post by mulluysavage on 2009-12-14
> **philinux said:**
> Forum etiquette. I posted the wrong thing hence snipped it out. 

After looking at this I would get rid of the space using Sys>admin>disk utility.

I don't have sys>admin>disk utility. I'm running Mythbuntu so I think it's an xfce thing.

---

### Post by mulluysavage on 2009-12-14
> **sisco311 said:**
> ```
UUID=0380-924F /media/My**\040**Book vfat rw 0 0
```


[noparse]
\040 - is an escape sequence. 040 is the ascii code, in octal(base 8) number system, of the space. The mount command interprets \040 as literal space in the mount point an not as a field separator.[/noparse]

We have a winner!

---

### Post by michaelzap on 2009-12-14
> **sisco311 said:**
> ```
UUID=0380-924F /media/My**\040**Book vfat rw 0 0
```


[noparse]
\040 - is an escape sequence. 040 is the ascii code, in octal(base 8) number system, of the space. The mount command interprets \040 as literal space in the mount point.[/noparse]

Yep - this definitely works, and enclosing the whole path in quotes usually does also.

---

### Post by ukripper on 2009-12-14
> **mulluysavage said:**
> We have a winner!

Give me my money!! <------[Stewie shouts]

---

