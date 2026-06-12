---
title: "New partition can't be used"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by vincent chin on 2009-03-04
I was using gparted to create a new logical partition with ext3 filesystem.But right now I not able to create/paste any file from/to the partition (/dev/sda3 with mount point /media/disk)

Thank you.

---

### Post by Bachstelze on 2009-03-04
If you want to give yourself access to the whole partition,

```
sudo chown `whoami`:`whoami` /media/disk
```

I suggest you read more about UNIX-style permissions. The [FreeBSD Handbook]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/permissions.html") might be a good starting point.

---

### Post by vincent chin on 2009-03-04
I have tried these two commands and remount,but still can't use on the partition

```

sudo chown 'whoami':'whoami' /media/disk
sudo chmod 777 /media/disk

```

---

### Post by taurus on 2009-03-04
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```
Do you have that partition mounted automatically each time you boot?

---

### Post by Bachstelze on 2009-03-04
> **vincent chin said:**
> I have tried these two commands and remount,but still can't use on the partition

```

sudo chown 'whoami':'whoami' /media/disk
sudo chmod 777 /media/disk

```

You mistyped the command. You must use backticks (`), not single quotes ('). Also, doing [font="monospace"]chmod 777[/font] would give write access to all the users on the system, which is most likely not what you want.

---

### Post by vincent chin on 2009-03-04
Nope.The partition is mounted mannually.

vincent@vincent-laptop:/$ sudo fdisk -l
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5078a71f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3499    28105686   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda3            3500       13995    84309120   83  Linux
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Partition table entries are not in disk order


```

vincent@vincent-laptop:/$ sudo blkid
```

/dev/sda1: UUID="8642d5a3-2ef5-4d64-8c1a-b99785a4c241" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="cb79729a-86f4-49a1-8fe7-542103f35a1d" 
/dev/sda3: UUID="ecf590d4-7943-44b8-9968-9c724f0577db" TYPE="ext3"

```

vincent@vincent-laptop:/$ cat /etc/fstab
```

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8642d5a3-2ef5-4d64-8c1a-b99785a4c241 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cb79729a-86f4-49a1-8fe7-542103f35a1d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

vincent@vincent-laptop:/$ df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              27G  4.0G   22G  16% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  260K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3              80G  184M   75G   1% /media/disk

```

vincent@vincent-laptop:/$ id
```

uid=1000(vincent) gid=1000(vincent) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(vincent)
```

---

### Post by taurus on 2009-03-04
Manually as in by hand or automount?

```
sudo chown vincent:vincent /media/disk
ls -la /media
```
If you mount it by hand, consider using another mount point since hal uses /media/disk (usually) as a mount point when you plug an external drive to your machine.

---

### Post by vincent chin on 2009-03-04
mannually by hand

---

### Post by vincent chin on 2009-03-04
> **taurus said:**
> Manually as in by hand or automount?

```
sudo chown vincent:vincent /media/disk
ls -la /media
```
If you mount it by hand, consider using another mount point since hal uses /media/disk (usually) as a mount point when you plug an external drive to your machine.

```

vincent@vincent-laptop:/$ ls -la /media
total 20
drwxr-xr-x  4 root    root    4096 2009-03-04 22:56 .
drwxr-xr-x 21 root    root    4096 2009-03-04 21:45 ..
lrwxrwxrwx  1 root    root       6 2009-02-16 06:04 cdrom -> cdrom0
drwxr-xr-x  2 root    root    4096 2009-02-16 06:04 cdrom0
drwxrwxrwx  3 vincent vincent 4096 2009-03-04 22:03 disk
-rw-r--r--  1 root    root      59 2009-03-04 22:56 .hal-mtab
-rw-------  1 root    root       0 2009-03-04 21:45 .hal-mtab-lock

```

How can the mount point be changed?

---

### Post by BLTicklemonster on 2009-03-04
Without your new drive mounted, edit fstab to this:


```

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8642d5a3-2ef5-4d64-8c1a-b99785a4c241 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda3        /media/disk     ext3    defaults        0       0
# /dev/sda5
UUID=cb79729a-86f4-49a1-8fe7-542103f35a1d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

save.

now in terminal

```

sudo mkdir /media/disk

```

then

```

sudo mount -a

```

See if that gets it.

---

### Post by vincent chin on 2009-03-04
Nope..It's having error on sudo mount /a

```

vincent@vincent-laptop:/$ sudo mount /a
[mntent]: line 1 in /etc/fstab is bad
mount: can't find /a in /etc/fstab or /etc/mtab

```

---

### Post by BLTicklemonster on 2009-03-04
lol  my bad

sudo mount -a


sorry about that.

---

### Post by taurus on 2009-03-04
> **BLTicklemonster said:**
> lol  my bad

sudo mount -a

sorry about that.

There is also a typo for an entry of **[COLOR="Blue"]/[/COLOR]**dev/sda3 in your previous post.

---

### Post by BLTicklemonster on 2009-03-04
Thanks. I'm in the dungeon where we keep the computers, and it's like a gazillion below zero down here, my fingers just keep wandering off on their own!

Here's what it should be:

> Without your new drive mounted, edit fstab to this:


```

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8642d5a3-2ef5-4d64-8c1a-b99785a4c241 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda3        /media/disk     ext3    defaults        0       0
# /dev/sda5
UUID=cb79729a-86f4-49a1-8fe7-542103f35a1d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

save.

now in terminal

```

sudo mkdir /media/disk

```

then

```

sudo mount -a

```

See if that gets it.

Also edited the original post.

---

