---
title: "Auto mount ntfs read only"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Sp4 on 2010-05-09
Hi 

I have just done a clean install to 10.4. Updated every thing got it running the way i like it and the way im used to when i hit a problem

In the past i use pysdm to mount my second drive that is formatted to ntfs, it's mounting on reboot but it's read only and the permissions tab on properties is blank with just the following text

> the permissions of "sdb5" could not be determined 

and if i try to move anything to it i get 

> Error while copying to "sdb5" The destination is read-only.

Any advice would be appreciated as this is where i keep all the music and films

Ta

---

### Post by cariboo on 2010-05-09
What does /etc/fstab look like?

---

### Post by Sp4 on 2010-05-10
Thank you for your time cariboo907

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid                                             0  0  
# / was on /dev/sda1 during installation
UUID=a3bcbb33-639b-4bdb-a003-882823813b36  /               ext4  errors=remount-ro                                               0  1  
# swap was on /dev/sda5 during installation
UUID=d406f4bb-ad53-4d6a-8e6d-f679b8db4e46  none            swap  sw                                                              0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8                                        0  0  
/dev/sdb5                                  /media/sdb5     ntfs  nls=iso8859-1,ro,users,umask=000,gid=users,user,owner,uid=root  0  0  
```

---

### Post by Sp4 on 2010-05-11
i noticed that the **ro** in the last line should be **rw**

solved

---

### Post by doogiekd on 2010-05-29
hi.

i had the same problem - external ntfs hard drive was read only. i changed the permissions with the the STORAGE DEVICE MANAGER and it worked for a period of time. perhaps it was changed with an update.

very frustrating.

so if you have an external ntfs drive and are having trouble with permissions - changing from a read only drive to writeable, then:

1. open terminal

2. run "sudo gedit /etc/fstab

3. change "ro" to "rw" in the line under the problem device.

---

