---
title: "cannot mount external hard drive"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by adamjkok on 2010-12-18
Hi, when attaching an external 1TB hard drive I was given (with a lot of files already on it), I got the following error:

"Unable to mount WD smartware - not authorized"

This seems strange considering that I'm logged in as the user that installed the system. Any pointers?

---

### Post by earthpigg on 2010-12-18
can you show us the results of this command?

```
cat /etc/fstab
```

---

### Post by adamjkok on 2010-12-18
> **earthpigg said:**
> can you show us the results of this command?

```
cat /etc/fstab
```


[COLOR=#000000][FONT=Arial]adam@lucid:~$ cat /etc/fstab[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# /etc/fstab: static file system information.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# Use 'blkid -o value -s UUID' to print the universally unique identifier[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# for a device; this may be used with UUID= as a more robust way to name[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# devices that works even if disks are added and removed. See fstab(5).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]proc            /proc           proc    nodev,noexec,nosuid 0       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# / was on /dev/sda1 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]UUID=81093392-d32e-4c7d-ac59-ec13e764a8b2 /               ext4    errors=remount-ro 0       1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# swap was on /dev/sda5 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]UUID=c402d937-3613-43c8-95d8-171bc858697d none            swap    sw              0       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]

---

### Post by earthpigg on 2010-12-19
well, nothing wrong with the fstab.

is this hard drive possibly over 95% full?

---

### Post by germanix on 2010-12-19
I had a similar problem where I could not mount an external drive as I was seen not to be the owner of the drive.
This solved the problem for me:
sudo chown username:username /media/WD smartware 

Maybe it helps you?

---

### Post by BbUiDgZ on 2010-12-19
if its an ntfs drive plug it into windows and unmount it properly

---

### Post by admiralspark on 2010-12-19
Also, and I'm not sure if this applies to your 1TB, but a 1TB MyBook (by WD) we have won't mount unless you use the authorization software from the 'cd' built into it's firmware. Windows automatically mounts it, but Linux (being more secure) doesn't do that. You might have to make a modified /etc/fstab.

Also, maybe post the output of 
```
lspci
```
when the drive is plugged in, so that we can see if the system registers it as a USB external device?

---

