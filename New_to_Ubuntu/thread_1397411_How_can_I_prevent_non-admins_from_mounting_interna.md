---
title: "How can I prevent non-admins from mounting internal partitions?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by KIAaze on 2010-02-03
How can I prevent non-admins from mounting internal partitions?
I want to allow use of USB sticks or external USB drives, but not the use of internal partitions, like the windows partition for example.

My current /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=0a03bba2-be0c-4f77-a393-dd39ff775ea9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=75eb4ad5-320f-4c6a-ae11-d0237997d55a /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=02b03bbd-b7e2-4ca4-8d01-aed5f9f0f650 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

edit:
Ok, problem partially solved:
I used [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/):
```
sudo apt-get install pysdm
```
and set the "nouser" option on /dev/sda1.

This changed my fstab to:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0
# / was on /dev/sda2 during installation
UUID=0a03bba2-be0c-4f77-a393-dd39ff775ea9  /              ext4         errors=remount-ro      0  1
# /home was on /dev/sda5 during installation
UUID=75eb4ad5-320f-4c6a-ae11-d0237997d55a  /home          ext4         defaults               0  2
# swap was on /dev/sda7 during installation
UUID=02b03bbd-b7e2-4ca4-8d01-aed5f9f0f650  none           swap         sw                     0  0
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0
/dev/sda1                                  /media/sda1    ntfs         nouser                 0  0

```
I can now only mount /dev/sda1 via:
```
sudo mount /dev/sda1
```

I cannot mount it via dolphin as admin-user anymore unfortunately.
Is there a way to fix this?

---

### Post by jken146 on 2010-02-03
> I cannot mount it via dolphin as admin-user anymore unfortunately.
Is there a way to fix this? 
You've just prevented all users (except root) from mounting it, so can't, no (I assume that by 'admin-user' you meant a user who is a sudoer rather than root).

---

### Post by KIAaze on 2010-02-03
Yes, I already knew that and I did indeed mean sudoers.

However, I still haven't found any solution.
I tried several different fstab options, tried it on ntfs and ext4 partitions (because apparently [ntfs is even more problematic]("http://www.tuxera.com/community/ntfs-3g-faq/#useroption")) and nothing worked so far.
My latest /etc/fstab lines:
```
/dev/sda1                                  /media_user    ntfs         ro,noauto,user,owner,uid=kiaaze  0  0
/dev/sda3                                  /media/sda3    ext4         group,noauto,user              0  0

```

The biggest progress I made is that I can get the error message given by dolphin by running "mount DEVICE" without sudo, so I'll be using that from now on for testing.
I've read through "man mount", but still haven't found anything that works.
It also seems to have something to do with "fuse", which I still haven't figured out yet.

> # If a device/partition is not listed in fstab ONLY ROOT may mount the device/partition.
# Users may mount a device/partition if the device is in fstab with the proper options. 

src: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

So how come I was able to mount them when they were not in fstab???

---

### Post by jken146 on 2010-02-03
By the way, why do you want to prevent some users from accessing this partition? Why not just use [file permissions]("http://www.tuxfiles.org/linuxhelp/filepermissions.html") to keep them from seeing what's there?

---

### Post by jken146 on 2010-02-03
> So how come I was able to mount them when they were not in fstab???

[FUSE]("http://en.wikipedia.org%2Fwiki%2FFilesystem_in_Userspace") allows users to "mount" certain kinds of things just for that one user. It's useful for things like network shares and is one way of mounting NTFS partitions. You can disable this on a per-user basis (look in the users management thingy in the System menu but it might create more problems than it solves.

---

