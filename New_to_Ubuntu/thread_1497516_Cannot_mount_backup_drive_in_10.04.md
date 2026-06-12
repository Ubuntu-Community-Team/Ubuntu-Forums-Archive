---
title: "Cannot mount backup drive in 10.04"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by UglyShirts on 2010-05-30
Please help!

I've been an Ubuntu user for some time, but last night, I just upgraded to Lynx from Hardy. And now I cannot mount my secondary hard drive. This is a big ol' drag, because I use the primary HS ONLY for OS boot/storage, and EVERYTHING else (photos, movies, music and all miscellaneous personal files) are on the second hard drive. 

I've searched, and I've searched, and I've tried everything. Gparted, Disk Utility, command line functions...And no joy. The utility either has an error every time I try to mount it (telling me it's already mounted when it isn't, and I can't access it), or every time I THINK I've succeeded, I've only mounted a second instance of the OS drive. Disk utility SEES it, and can scan/access/read it, but it won't let me do the same. 

I'm at the end of my rope and my hope, so I'm turning to the community for assistance. Please, if you can, toss me a bone, and help me figure out what I'm doing wrong.

---

### Post by Morbius1 on 2010-05-30
Post the output of these commands so we can see what's up:

```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by UglyShirts on 2010-05-30
> **Morbius1 said:**
> Post the output of these commands so we can see what's up:

Thanks. Here ya go:

```
/dev/sda1: LABEL="Archive" UUID="C6EE0261EE0249DF" TYPE="ntfs" 
/dev/sdb1: UUID="e735a73e-3b41-4ddc-bf54-b262b069cdd9" TYPE="ext4" 
/dev/sdb5: UUID="a20da5eb-b58b-4a10-932b-be6fcfd150d1" TYPE="swap" 

```

---

### Post by Morbius1 on 2010-05-30
What about the other two commands:
```
cat /etc/fstab
mount
```

I'm assuming sda1 is the secondary drive?

---

### Post by UglyShirts on 2010-05-30
> **Morbius1 said:**
> What about the other two commands:
```
cat /etc/fstab
mount
```

I'm assuming sda1 is the secondary drive?

Whoops, sorry. 

cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a20da5eb-b58b-4a10-932b-be6fcfd150d1 none            swap    sw              0       0

```

mount:

```
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jim)
/dev/sda1 on / type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

And yes...The secondary drive is the 160g "Archive" drive, and it's coming up as sda1.

Thanks.

---

### Post by CharlesA on 2010-05-30
See what it says with this:

```
sudo fdisk -l
```

It looks like it's trying to mount /dev/sda1 as the OS drive.

Also looks like there are two things mounted to "/"

---

### Post by UglyShirts on 2010-05-30
> **CharlesA said:**
> See what it says with this:

```
sudo fdisk -l
```

It looks like it's trying to mount /dev/sda1 as the OS drive.

Also looks like there are two things mounted to "/"

Here ya go:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a3d5504

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20673   156287848+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004d83b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4658    37410816   83  Linux
/dev/sdb2            4658        4863     1648641    5  Extended
/dev/sdb5            4658        4863     1648640   82  Linux swap / Solaris

```

And yes...It probably is seeing the files drive as bootable. I'm thinking part of the problem with me trying to mount it NOW is that some of the things I've tried to do in order to fix the problem may have configured certain parameters incorrectly...and I'm not skilled enough to know which, nor how to toggle them back.

---

### Post by Morbius1 on 2010-05-30
I think your only way out of this is to modify a line in your fstab:
This:
> [COLOR=Blue]/dev/sda1[/COLOR]       /               ext4    errors=remount-ro 0       1Should be:
> UUID=e735a73e-3b41-4ddc-bf54-b262b069cdd9       /               ext4     errors=remount-ro 0       1After you save it I don't think you have any other choice but to reboot.

Not exactly sure how you have two partitions mounted to "/" but I think the best thing to do is eliminate the legacy designations ( i.e., sda1, sdb1, etc..) from fstab.

---

### Post by CharlesA on 2010-05-30
Try this:

Backup fstab.

Add the UUID for the root drive to fstab where /dev/sda1 is.

UUID=e735a73e-3b41-4ddc-bf54-b262b069cdd9

Reboot and see what happens.

---

### Post by UglyShirts on 2010-05-30
At the risk of sounding like a giant, wet-behind-the-ears noob, how would I go about doing these things, step-by-step?

Sorry if that tests your patience, I just don't want to further bork the system by doing something else even a little bit incorrectly.

---

### Post by CharlesA on 2010-05-30
Make a backup of fstab like so:

```
cp /etc/fstab ~/fstab.bk
```

Then open fstab:
```
gksu gedit /etc/fstab
```

Add the this where /dev/sda1 is:

```
UUID=e735a73e-3b41-4ddc-bf54-b262b069cdd9
```

Then reboot.

---

### Post by Morbius1 on 2010-05-30
Open **Terminal **
Type **gksu gedit /etc/fstab**

This will get you into an editor as root. You can place a # in front of the current line in fstab so that it goes from this:
>  [COLOR=Black]/dev/sda1[/COLOR]       /               ext4     errors=remount-ro 0       1                      
To this:
> #[COLOR=Black]/dev/sda1[/COLOR]       /               ext4     errors=remount-ro 0       1Then just copy and paste the following to the end of the file:
```
UUID=e735a73e-3b41-4ddc-bf54-b262b069cdd9 / ext4   errors=remount-ro 0       1
```Save the file, exit gedit, and reboot.

[COLOR=Blue]EDIT:[/COLOR] CharlesA, It looks like were stepping all over each other today. Sorry. At least we're not disagreeing with each other:)

---

### Post by UglyShirts on 2010-05-30
Just did this. 

Rebooting. I'll let you guys know what happens. 

Thanks for the assistance!

---

### Post by CharlesA on 2010-05-30
> **Morbius1 said:**
> 
[COLOR=Blue]EDIT:[/COLOR] CharlesA, It looks like were stepping all over each other today. Sorry. At least we're not disagreeing with each other:)

It happens. :)

---

### Post by UglyShirts on 2010-05-30
You guys are my heroes. Archive drive is mounted, up, and running. 

[IMG]http://i47.tinypic.com/16119tt_th.png[/IMG]

Can't thank you enough for all the help!

---

### Post by Morbius1 on 2010-05-30
Whew :biggrin:

---

### Post by CharlesA on 2010-05-30
Don't forget to mark the thread as solved. :-)

---

### Post by UglyShirts on 2010-05-30
> **CharlesA said:**
> Don't forget to mark the thread as solved. :-)

Thanks for the reminder. :)

---

