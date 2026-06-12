---
title: "New Hard drive needs permission"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by mikee55 on 2009-09-12
I have 3 hard drives. 20 Gb resides Ubuntu X64. 120 GB Storage and 160 Gb storage. The 160 GB holds NTFS from being my media storage in WinXP. The 120 GB held XP and the 20 GB just acquired. I thought I should loose the NTFS of the 120 GB and make it Reiserfs. I installed GParted and formatted the drive, however it says I have to have permission to move stuff to it. So, I turned to ext 2 with GParted. It says it has a boot flag and I still have an 8mb partition left over from the WinXP  installation?

If I have GParted permission to change a drives partition, why can't I move files to it???

Mike:D

---

### Post by nothingspecial on 2009-09-12
Assuming the drive is mounted at /media/disk and your username is mike .....
```

sudo chown -R mike:mike /media/disk/
```

```
sudo chmod -R 755 /media/disk
```

Change the names to protect the innocent (or at least assign the correct ownership and permissions to the correct drive)

---

### Post by mikee55 on 2009-09-12
lounge-pc@lounge-pc-desktop:~$ sudo chown -R lounge-pc:lounge-pc /Storage 2
chown: cannot access `/Storage': No such file or directory
chown: cannot access `2': No such file or directory
lounge-pc@lounge-pc-desktop:~$ 

The drive is called Storage 2

??

Mike :)

---

### Post by twright on 2009-09-12
You can find out the available drives using:
```
ls /media/
```

edit:
You can also change the permissions by right clicking and going into properties.

---

### Post by nothingspecial on 2009-09-12
You need to escape the space. 
```

sudo chown -R lounge-pc:lounge-pc /media/Storage\ 2
```

Notice the \ inbetween Storage and 2.

---

### Post by nothingspecial on 2009-09-12
> **mikee55 said:**
> lounge-pc@lounge-pc-desktop:~$ 

If I looked properly I could see that lounge-pc is the username.

---

### Post by mikee55 on 2009-09-12
Don't have a user name :)

---

### Post by twright on 2009-09-12
> **mikee55 said:**
> Don't have a user name :)
You must otherwise you would not have a user ;-)

---

### Post by mikee55 on 2009-09-13
Sorry been sleeping.

Hello, I think lounge-pc is the user name, same as the computer name. I log on without a password, too. Security is not an issue at this time. When I have Ubuntu doing everything I want/need, then I'll go secure.

lounge-pc@lounge-pc-desktop:~$ sudo chown -R lounge-pc:lounge-pc /media/Storage\2[sudo] password for lounge-pc: 
chown: cannot access `/media/Storage2': No such file or directory
lounge-pc@lounge-pc-desktop:~$ 
:D

Mike:)

---

### Post by twright on 2009-09-13
> **mikee55 said:**
> Sorry been sleeping.

Hello, I think lounge-pc is the user name, same as the computer name. I log on without a password, too. Security is not an issue at this time. When I have Ubuntu doing everything I want/need, then I'll go secure.

lounge-pc@lounge-pc-desktop:~$ sudo chown -R lounge-pc:lounge-pc /media/Storage\2[sudo] password for lounge-pc: 
chown: cannot access `/media/Storage2': No such file or directory
lounge-pc@lounge-pc-desktop:~$ 
:D

Mike:)
Well the should not be an issue at this stage. Even if you do not use a password when you log in you still have a user name.

The issue is that you are still getting the name wrong,
you need to type exactly this:
```
sudo chown -R lounge-pc:lounge-pc "/media/Storage 2"
```

---

### Post by nothingspecial on 2009-09-13
> **mikee55 said:**
> Sorry been sleeping.

Hello, I think lounge-pc is the user name, same as the computer name. I log on without a password, too. Security is not an issue at this time. When I have Ubuntu doing everything I want/need, then I'll go secure.

lounge-pc@lounge-pc-desktop:~$ sudo chown -R lounge-pc:lounge-pc /media/Storage\2[sudo] password for lounge-pc: 
chown: cannot access `/media/Storage2': No such file or directory
lounge-pc@lounge-pc-desktop:~$ 
:D

Mike:)

That'll work too. The problem is that linux  doesn`t like spaces in directory or file names. You have to escape it. One method like above is to put it in quotes. The other way is to escape it with a \

You still have to have the space though. /media/Storage\ 2 not /media/Storage\2.

Hope that clears it up.

---

### Post by mikee55 on 2009-09-13
Just says Storage 2 no file or directory:confused:

Mike

---

### Post by nothingspecial on 2009-09-13
You need to find where Storage\ 2 exists in your file system.

The path to a directory always starts with /

That is root the start of everything.
```

cd /
``` will take you to root

```
ls
``` will list every directory "in" the root directory. Your`s should look similar to mine
```

bin   cdrom  etc   initrd.img      lib         media  opt   root  selinux  sys  usr  vmlinuz
boot  dev    home  initrd.img.old  lost+found  mnt    proc  sbin  srv      tmp  var  vmlinuz.old
```

Removable drives are usually mounted in /media like so

```
ls /media 
backup  cdrom  cdrom0  cdrom1  cdrom2  drive  floppy  floppy0  ipod  usb
```

There`s my backup drives, my cdroms and floppys, my ipod, usb stick(usb) and my external hdd(drive)

What does it say if you type ```
ls /media
```

---

### Post by mikee55 on 2009-09-13
lounge-pc@lounge-pc-desktop:~$ ls
Desktop    examples.desktop  Pictures  Templates
Documents  Music             Public    Videos
lounge-pc@lounge-pc-desktop:~$ ls /media
cdrom  cdrom0
lounge-pc@lounge-pc-desktop:~$ 


Don't look right, nothingspecial?????

Mike:confused:

---

### Post by nothingspecial on 2009-09-14
Where is it then? Post the output of

```
sudo fdisk -l
```

and 

```
mount
```

please

---

### Post by mikee55 on 2009-09-14
lounge-pc@lounge-pc-desktop:~$ sudo fdisk -l
[sudo] password for lounge-pc: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2b4fcec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf59bf59b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c19e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14592   117210208+  83  Linux
/dev/sdc2           14593       14593        8032+  83  Linux
lounge-pc@lounge-pc-desktop:~$ 


lounge-pc@lounge-pc-desktop:~$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lounge-pc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lounge-pc)
lounge-pc@lounge-pc-desktop:~$

There you go, hope this helps. I've come back from work to find no bookmarks in Firefox, I've had countless problems with my Graphics card and Compiz  ???

---

### Post by nothingspecial on 2009-09-14
Ok. fdisk lists your 120gig drive as /dev/sdc1

But mount reports it as not mounted.

Does an icon for it appear in your places menu?

If it does then click it. Then ls /media again to assertain the correct path.

If not you are going to have to manually mount it.

```
sudo mkdir /media/storage2
```
```

sudo mount -t ext2 /dev/sdc1 /media/storage2
```


[COLOR="Red"]note I have left the space out[/COLOR]

```
sudo chown -R lounge-pc:lounge-pc /media/storage2
```
```
sudo chmod -R 755 /media/storage2
```

---

### Post by mikee55 on 2009-09-14
Solved:lolflag:

Umm, I cheated. I dug out my copy of PCLinuxOs 2007 live cd,:biggrin: and used Harddrak to format the drive. It worked\\:D/


Now, next. Why is it that when I turn on Extra Visual Effects, I'm loosing Minimize window, Maximize window and Close window buttons? This also seems to happen when I run a second monitor with seperate x screens???:confused:

The reboot has fixed my lost bookmarks in Firefox.:)

---

### Post by nothingspecial on 2009-09-14
```
sudo apt-get install compizconfig-settings-manager
```

If you`ve not got it already.

Then in your menus system > preferences > compizconfig settings manager. Then make sure the window decoration plugin has a tick next to it.

---

