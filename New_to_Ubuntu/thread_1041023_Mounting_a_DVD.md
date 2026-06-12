---
title: "Mounting a DVD"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by a.v.l on 2009-01-16
I can't seem to open a booklet sent to me on a CD. Can someone help by explaining how to do this please?  If I go to Places > Computer I can see the DVD drive there but when I click on it it tells me "unable to mount location -cannot mount file" Right clicking on the drive and going to mount volume does nothing either.

---

### Post by a.v.l on 2009-01-16
> **a.v.l said:**
> I can't seem to open a booklet sent to me on a CD. Can someone help by explaining how to do this please?  If I go to Places > Computer I can see the DVD drive there but when I click on it it tells me "unable to mount location -cannot mount file" Right clicking on the drive and going to mount volume does nothing either.

Just to add further information I've been able to open and read the content of this CD using Vista. The file is a PDF file. How doesn't it open in Ubuntu and why won't the disc mount when other CD's and DVD do :P?

---

### Post by Michael.Godawski on 2009-01-16
hi,

can you please post the output of these commands:
```

cat /etc/fstab
mount
ls -la /media
```

---

### Post by a.v.l on 2009-01-16
> **Michael.Godawski said:**
> hi,

can you please post the output of these commands:
```

cat /etc/fstab
mount
ls -la /media
```

Now that's odd. I'm unable to open the Terminal. When I try I just open an empty white box with nothing else not even text in it.

---

### Post by hessiess on 2009-01-16
> **a.v.l said:**
> Now that's odd. I'm unable to open the Terminal. When I try I just open an empty white box with nothing else not even text in it.

ctrl -> alt -> f1(drop back to a BASH terminal), log in. 

(replace --user-- with your username)
```
cat /etc/fstab > /home/--user--/fstab.txt
mount > /home/--user--/mount.txt
ls -la /media > /home/--user--/media.txt
```

ctrl -> alt -> f7 (go back to the GUI)

the results of the commands shounld be in:
home/--user--/fstab.txt
home/--user--/mount.txt
home/--user--/media.txt

---

### Post by a.v.l on 2009-01-16
> **hessiess said:**
> ctrl -> alt -> f1(drop back to a BASH terminal), log in. 

(replace --user-- with your username)
```
cat /etc/fstab > /home/--user--/fstab.txt
mount > /home/--user--/mount.txt
ls -la /media > /home/--user--/media.txt
```

ctrl -> alt -> f7 (go back to the GUI)

the results of the commands shounld be in:
home/--user--/fstab.txt
home/--user--/mount.txt
home/--user--/media.txt

Unfortunatly I'm still unable to open the terminal. One other issue I've notice over the last day is that I've lost the closing cross and minimise icons in the top right hand corner of opened windows, I'm not sure if this is relevant.

---

### Post by hessiess on 2009-01-16
> **a.v.l said:**
> Unfortunatly I'm still unable to open the terminal. One other issue I've notice over the last day is that I've lost the closing cross and minimise icons in the top right hand corner of opened windows, I'm not sure if this is relevant.

Try disabling visual effects (of they arn't already)
system ->preferences ->appearance ->visual effects ->none.

---

### Post by a.v.l on 2009-01-16
> **hessiess said:**
> Try disabling visual effects (of they arn't already)
system ->preferences ->appearance ->visual effects ->none.

All disabled but still the same I'm afraid.

---

### Post by a.v.l on 2009-01-16
> **a.v.l said:**
> All disabled but still the same I'm afraid.

My apologies I stand corrected, they have suddenly corrected themselves. Much appreciated, now to go back to my DVD issue earlier.

---

### Post by a.v.l on 2009-01-16
> **Michael.Godawski said:**
> hi,

can you please post the output of these commands:
```

cat /etc/fstab
mount
ls -la /media
```

cat /etc/fstab
mount
ls -la /media

**********************************************************************

User name:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=251b3377-d0c9-44cb-abff-e03da9ff7779 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=E4701D71701D4BA4 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=bed57349-b574-4c52-b41e-c8e848c8ebe2 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0alan@user-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
user@user-desktop:~$ ls -la /media
user@user-desktop:~$

---

### Post by mohitw on 2009-01-17
Hello , I am not able to mount my CD drive . It seems that when I my /etc/fstab, the contents are:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=c439a46e-5b91-4d74-8c57-1c873e06d6cc /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

when I checked  /dev for scd0 ..it seems there is no scd0 file.
Please help

---

### Post by mohitw on 2009-01-17
> **mohitw said:**
> Hello , I am not able to mount my CD drive . It seems that when I my /etc/fstab, the contents are:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=c439a46e-5b91-4d74-8c57-1c873e06d6cc /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

when I checked  /dev for scd0 ..it seems there is no scd0 file.
Please help
Also, forgot to mention that I am having ubuntu 8.04 edition on amd 64 PC (dual boot with Vista).

---

### Post by fuser312 on 2009-01-17
install a graphical tool for mounting. look in synaptic, type ntfs in search box. 
give this a try, a graphical tool is always more helpful.

---

### Post by a.v.l on 2009-01-17
> **fuser312 said:**
> install a graphical tool for mounting. look in synaptic, type ntfs in search box. 
give this a try, a graphical tool is always more helpful.

Thanks but still can't read a CD or DVD :(

---

