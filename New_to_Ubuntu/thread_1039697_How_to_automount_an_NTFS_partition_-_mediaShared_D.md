---
title: "How to automount an NTFS partition - /media/Shared Data"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Mylorharbour on 2009-01-14
[COLOR="Blue"][Solved][/COLOR]

On my dual-boot XP/Intrepid machine I have an NTFS shared partition. It is used for document and multimedia files which are accessible from both operating systems. The mount point in Ubuntu is /media/Shared Data (yes there is a space between Shared and Data). It appears in the Places menu and clicking on it will mount it and put it on the desktop.

In trying to put an entry in fstab to mount this automatically I modified a line from an Ubuntu book I was bought for Christmas but that plainly doesn't work. Knowing what you now know about this partition could someone post a suitable line for use in fstab probably based on the following which is the modified line refered to?

UUID=0414E80C14E80312 /media/[COLOR="Red"]Shared Data[/COLOR] ntfs [COLOR="Blue"]defaults,nls=utf8,umask=007,gid=46 0 0[/COLOR]

I don't pretend to understand what the entries in blue mean but the bit in red I tried to address by using \040 instead of the space.

I'd prefer to keep the name as /media/Shared Data as I have Windows Media Player and Amarok and other applications referencing that as the location and I wonder what would happen if I renamed it. That said, if I do have to rename it how should I go about it?

---

### Post by jemate18 on 2009-01-14
> **Mylorharbour said:**
> On my dual-boot XP/Intrepid machine I have an NTFS shared partition. It is used for document and multimedia files which are accessible from both operating systems. The mount point in Ubuntu is /media/Shared Data (yes there is a space between Shared and Data). It appears in the Places menu and clicking on it will mount it and put it on the desktop.

In trying to put an entry in fstab to mount this automatically I modified a line from an Ubuntu book I was bought for Christmas but that plainly doesn't work. Knowing what you now know about this partition could someone post a suitable line for use in fstab probably based on the following which is the modified line refered to?

UUID=0414E80C14E80312 /media/[COLOR="Red"]Shared Data[/COLOR] ntfs [COLOR="Blue"]defaults,nls=utf8,umask=007,gid=46 0 0[/COLOR]

I don't pretend to understand what the entries in blue mean but the bit in red I tried to address by using \040 instead of the space.

I'd prefer to keep the name as /media/Shared Data as I have Windows Media Player and Amarok and other applications referencing that as the location and I wonder what would happen if I renamed it. That said, if I do have to rename it how should I go about it?


I think the  /media/[COLOR="Red"]Shared Data[/COLOR] is  the problem, you should use /media/Shared\ Data 

You need to put a "\" before a space character. Please try

---

### Post by Mylorharbour on 2009-01-15
I tried that Jemate. It doesn't automount and I get this error when I click on Shared Data in 'Places':

Cannot mount volume
Unable to mount the volume 'Shared Data'
Details
[mntent]: line 13 in /etc/fstab is bad
mount: can't find /media/Shared\ in /etc/fstab or /etc/mtab


The fstab listing looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=4f7acef9-9754-4136-aca1-4a5d0efd1567 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=e68b88ca-3f44-4e13-bad3-3fd13e972ee2 /home           ext3    relatime        0       2
# /dev/sda6
UUID=5dfe6ec0-57e3-47c1-a94d-f93184845134 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Doesn't work    
UUID=0414E80C14E80312 /media/Shared\ Data ntfs defaults,nls=utf8,umask=007,gid=46 0 0


Does that look ok to you?

---

### Post by sisco311 on 2009-01-15
try:> UUID=0414E80C14E80312 /media/Shared**\040**Data ntfs defaults,nls=utf8,umask=007,gid=46 0 0

you need to convert the space to the octal representation of the space "\040".
spaces are used as delimiters in fstab.

---

### Post by talsemgeest on 2009-01-15
> **Mylorharbour said:**
> I tried that Jemate. It doesn't automount and I get this error when I click on Shared Data in 'Places':

Cannot mount volume
Unable to mount the volume 'Shared Data'
Details
[mntent]: line 13 in /etc/fstab is bad
mount: can't find /media/Shared\ in /etc/fstab or /etc/mtab


The fstab listing looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=4f7acef9-9754-4136-aca1-4a5d0efd1567 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=e68b88ca-3f44-4e13-bad3-3fd13e972ee2 /home           ext3    relatime        0       2
# /dev/sda6
UUID=5dfe6ec0-57e3-47c1-a94d-f93184845134 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Doesn't work    
UUID=0414E80C14E80312 /media/Shared\ Data ntfs defaults,nls=utf8,umask=007,gid=46 0 0


Does that look ok to you?
Also, change "ntfs" to "ntfs-3g".

---

### Post by sisco311 on 2009-01-15
> **talsemgeest said:**
> Also, change "ntfs" to "ntfs-3g".

ntfs works as well, since ?gutsy?

---

### Post by Mylorharbour on 2009-01-15
Ok I tried that but it still didn't mount. Clicked on 'Shared Data' in 'Places' again and got these error messages:

Cannot mount volume.
You are not privileged to mount the volume 'Shared Data'.

Then a few seconds later..........

Unable to mount Shared Data
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

The fstab entry is now.....
UUID=0414E80C14E80312 /media/Shared\040Data ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0

---

### Post by sisco311 on 2009-01-15
strange.

make sure that the mount point exist:
```
sudo mkdir "/media/Shared Data"
```

mount the partition:
```
sudo mount -a
```

next time you boot everything should be okay.

---

### Post by Shazaam on 2009-01-15
I don't know if this will help you or not (and it CAN cause problems if used incorrectly). There is an app called pysdm in the repos. It is a gui program for editing fstab. It shows as "Storage Device Manager" in the System>Administration menu after install.

---

### Post by drs305 on 2009-01-15
> **Mylorharbour said:**
> Ok I tried that but it still didn't mount. Clicked on 'Shared Data' in 'Places' again and got these error messages:

Cannot mount volume.
You are not privileged to mount the volume 'Shared Data'.

Then a few seconds later..........

The fstab entry is now.....
UUID=0414E80C14E80312 /media/Shared\040Data ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0

In that entry, you are still not the owner ("you are not privileged...") and so only root can mount it. Add yourself as the owner at mount time by changing it to the following. This assumes you are uid 1000, If you aren't sure, run "id" in terminal. "user" will also allow you to mount it - you can allow yourself to mount it with the uid=1000, or allow anyone to mount it with "user", or both.

```

UUID=0414E80C14E80312 /media/Shared\040Data ntfs-3g defaults,**uid=1000,user,**nls=utf8,umask=007,gid=46 0 0

```

---

### Post by bioshake on 2009-01-15
> **Mylorharbour said:**
> On my dual-boot XP/Intrepid machine I have an NTFS shared partition. It is used for document and multimedia files which are accessible from both operating systems. The mount point in Ubuntu is /media/Shared Data (yes there is a space between Shared and Data). It appears in the Places menu and clicking on it will mount it and put it on the desktop.

In trying to put an entry in fstab to mount this automatically I modified a line from an Ubuntu book I was bought for Christmas but that plainly doesn't work. Knowing what you now know about this partition could someone post a suitable line for use in fstab probably based on the following which is the modified line refered to?

UUID=0414E80C14E80312 /media/[COLOR="Red"]Shared Data[/COLOR] ntfs [COLOR="Blue"]defaults,nls=utf8,umask=007,gid=46 0 0[/COLOR]

I don't pretend to understand what the entries in blue mean but the bit in red I tried to address by using \040 instead of the space.

I'd prefer to keep the name as /media/Shared Data as I have Windows Media Player and Amarok and other applications referencing that as the location and I wonder what would happen if I renamed it. That said, if I do have to rename it how should I go about it?

Do you have a problem related to a CIFS VFS crash on reboot or reset with this setup?

---

### Post by sisco311 on 2009-01-15
never mind

---

### Post by Mylorharbour on 2009-02-18
All sorted now. I just renamed the folder to 'Shared' in XP. It would have been good to get Ubuntu to accept the 'Shared Data' folder but it was not to be.

---

### Post by Mylorharbour on 2009-02-23
Just a tip for dual-booters who find that occasionally their Shared partition won't mount or automount, it may be that Windows was hibernated when you last used it which seems to lock-out partitions it has access to.

---

### Post by Miljet on 2009-02-23
Maybe I am missing the whole point here, but it seems to me that the "/media/Shared Partition" part of the fstab file is just a mount point. The mount point can be anything you want, it doesn't have to match the name of the partition being mounted. In other words, the UUID identifies the partition to be mounted, and the /media/Shared Partition identifies where to mount it.

So the simple solution is to make a new mount point (without spaces) and use it as a mount point instead. And the above suggestion to add "users" to the options allow you to mount it without root permissions.

---

