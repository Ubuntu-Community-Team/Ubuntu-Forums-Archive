---
title: "/2 not ready"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by albert s on 2010-10-23
when I boot I get the message " /2 not ready " and some other stuff,
"press S to skip or M for manual recovery"
I added a 2nd hard drive and its been since that,
my 2nd hard drive doesnt auto mount,
I know I shouldnt have just added it but any help gratefully received.
thanks.

---

### Post by Hippytaff on 2010-10-23
what does
```

sudo fdisk -l

```
look like?

---

### Post by albert s on 2010-10-23
marko@marko-desktop:~$ sudo fdisk -l
[sudo] password for marko: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000943bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9726    78124063+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9250cd27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1993    16000000   83  Linux
/dev/sdb2            1993        9729    62140260    5  Extended
/dev/sdb5            1993        2236     1951744   82  Linux swap / Solaris
/dev/sdb6            2236        9729    60187491   83  Linux
marko@marko-desktop:~$ 


is this what you need,?

---

### Post by jmszr on 2010-10-23
albert s,

This will give you instructions on adding a new hard drive including how to set up the automount: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by Hippytaff on 2010-10-23
> 
is this what you need,?

Was wondering if it showed up, but no...the help link above will be what your looking for :-)

---

### Post by sikander3786 on 2010-10-23
If you can't figure it out from the link provided by **jmszr**, post the output of

```
cat /etc/fstab
```

And

```
sudo blkid
```

---

### Post by albert s on 2010-10-23
marko@marko-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=9cc9c160-0b81-4aa1-a582-32fe3cecb5a7 /               ext4    errors=remount-ro 0       1
# /2 was on /dev/sda5 during installation
UUID=4ffe6784-96a9-48b3-8356-eecaf58d333c /2              ext4    defaults        0       2
# /home was on /dev/sdb6 during installation
UUID=614626ac-6d84-4609-8405-b7ad2a5105e9 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=b127ae24-7c41-43f4-8cf4-63e4a7ce2797 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=a0809c4b-328e-42e2-9323-759c69391969 none            swap    sw              0       0




marko@marko-desktop:~$ sudo blkid
/dev/sda1: UUID="45ef24f4-6732-49bd-8a57-b061bab8195e" TYPE="ext4" 
/dev/sdb1: UUID="9cc9c160-0b81-4aa1-a582-32fe3cecb5a7" TYPE="ext4" 
/dev/sdb5: UUID="a0809c4b-328e-42e2-9323-759c69391969" TYPE="swap" 
/dev/sdb6: UUID="614626ac-6d84-4609-8405-b7ad2a5105e9" TYPE="ext4" 
marko@marko-desktop:~$ 



the screenshot I get is,

BTW I would just like the drive labelled 2 and ext4,
am I doing this wrong or should I just do an ext3 and leave it as newdrive.?

---

### Post by sikander3786 on 2010-10-23
UUIDs don't match.

Backup /etc/fstab by,

```
sudo cp /etc/fstab /etc/fstab.old
```

Edit by,

```
gksudo gedit /etc/fstab
```

Change the line

```
UUID=4ffe6784-96a9-48b3-8356-eecaf58d333c /2 ext4 defaults 0 2
```

to

```
UUID=45ef24f4-6732-49bd-8a57-b061bab8195e /2 ext4 defaults 0 2
```

Save, close and reboot to see it it works now.

---

### Post by albert s on 2010-10-23
> **sikander3786 said:**
> UUIDs don't match.

Backup /etc/fstab by,

```
sudo cp /etc/fstab /etc/fstab.old
```Edit by,

```
gksudo gedit /etc/fstab
```Change the line

```
UUID=4ffe6784-96a9-48b3-8356-eecaf58d333c /2 ext4 defaults 0 2
```to

```
UUID=45ef24f4-6732-49bd-8a57-b061bab8195e /2 ext4 defaults 0 2
```Save, close and reboot to see it it works now.


SUPERSTAR
its all OK now, you have no idea how nervous I still am about deleting and changing things I still am.
worked 100%,
thank you.
why doesnt this forum have a thanks button?

---

### Post by cariboo on 2010-10-23
What some of us do is make a backup of the file to be edited, before making any changes. that way you can go back to the original file if the changes you made don't work out.

---

### Post by sikander3786 on 2010-10-24
> **cariboo907 said:**
> What some of us do is make a backup of the file to be edited, before making any changes. that way you can go back to the original file if the changes you made don't work out.
```
sudo cp /etc/fstab /etc/fstab.old
```

Isn't this what you are talking about?

---

