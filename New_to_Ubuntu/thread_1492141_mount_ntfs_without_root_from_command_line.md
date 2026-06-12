---
title: "mount ntfs without root from command line"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by zetharx on 2010-05-24
I have found that if I do not put my ntfs partition in fstab, i can mount it simply through the nautilus "places" list.  when i click on the drive to mount and open it, it will automatically mount to /media/VOLUME_LABEL, the directory will be read/writeable, and this can be done without root access.

I would like to be able to auto-mount this drive as described on startup.  No root access, no fstab, just as if i had clicked the drive on "places".  Can anyone help me figure out a way to do so?

Also, as a note, anytime the drive is actually in my fstab with the 'user' option and I try to mount or unmount without root access, I get the following error message.

```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```

Can anyone tell me why this doesn't happen when the drive is not in fstab?

---

### Post by nhasian on 2010-05-24
I'm a little confused.  If you say you want your drive to be auto-mounted on startup, why don't you put it in your /etc/fstab?

if your having trouble setting it up in your /etc/fstab, please give us the output of these terminal commands so we can help you:

```
cat /etc/fstab
```
```
sudo blkid
```
```
sudo fdisk -l
```

If you want to be able to mount without privileged access then you will need to edit your /etc/sudoers file

more information can be found [here]("http://ubuntuforums.org/showthread.php?t=1132821").

I just came across this method of mounting partitions with a gui that you may be interested in:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by zetharx on 2010-05-24
fstab

```
# /etc/fstab: static file system information.
#
# <file system>					<mount point>			<type>	<options>					<dump>  <pass>
proc						/proc				proc	defaults					0	0
# main ext3
UUID=a12c6ac2-a62f-4775-9ac0-6fae667f07a8	/				ext3	relatime,errors=remount-ro			0	1
# swap
UUID=489b073a-fa4e-4ccb-8897-5d2d3dd42338	none				swap	sw						0       0

#windowsxp
UUID=E0A038D5A038B43E				/media/WinXP			ntfs	user,uid=1000,rw,sync				0	2

#dvd drives
/dev/scd0					/media/cdrom0			udf,iso9660 user,noauto,exec,utf8			0	0
/dev/scd1					/media/cdrom1			udf,iso9660 user,noauto,exec,utf8			0	0

```


blkid

```
/dev/sdb1: LABEL="WinXP" UUID="E0A038D5A038B43E" TYPE="ntfs" 
/dev/sdb5: LABEL="ubuntu" UUID="a12c6ac2-a62f-4775-9ac0-6fae667f07a8" TYPE="ext3" 
/dev/sdb6: UUID="489b073a-fa4e-4ccb-8897-5d2d3dd42338" TYPE="swap"
``` 

fdisk

```
Disk /dev/sdb: 73.5 GB, 73543163904 bytes
255 heads, 63 sectors/track, 8941 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00730072

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3841    30852801    7  HPFS/NTFS
/dev/sdb2            3842        8941    40965750    f  W95 Ext'd (LBA)
/dev/sdb5            3842        8759    39503803+  83  Linux
/dev/sdb6            8760        8941     1461883+  82  Linux swap / Solaris

```

I want to automount the partition, but if I do it through fstab, I end up with undesired permissions.

The deal is this.  I have seen it mount beautifully when I comment out the relevant line from fstab

```
#windowsxp
#UUID=E0A038D5A038B43E				/media/WinXP			ntfs	user,uid=1000,rw,sync				0	2
```

and after I save that change to fstab, I open a Nautilus window and click the drive in the list of places (called "WinXP").  It mounts where I want, how I want, with all the permissions I want.  I just can't seem to match this behavior with any combination of options on an fstab line.

As far as the automount, I am okay with just calling a script on boot-up using Startup Applications which runs a mount command.  I would just like to have it mounted the way I want after I boot without needing to click the icon in "places".

---

### Post by zetharx on 2010-05-24
By the way, you will notice that I am mounting using UUID's.  I chose this because I tend to move disks around, plugging and unplugging.  I assumed that the best way to keep track of which disk was which was by the UUID because I am afraid that the system will mix two drives between /dev/sdc and /dev/sdd or something like that.  Is there a better solution for keeping drives from being mixed up?

Oh and thank you for your time on this =).  I do appreciate all the help that I get.

---

### Post by zetharx on 2010-05-25
bump

---

### Post by Morbius1 on 2010-05-25
Change this:
> UUID=E0A038D5A038B43E    /media/WinXP    ntfs    user,uid=1000,rw,sync    0    2To this:
> UUID=E0A038D5A038B43E /media/WinXP ntfs defaults,nls=utf8,umask=000,uid=1000 0 0In a terminal:
```
sudo umount /media/WinXP
sudo mount -a
```Now see if the /media/WinXP is more of what you had in mind.

---

### Post by bodhi.zazen on 2010-05-25
> **Morbius1 said:**
> Change this:
To this:
In a terminal:
```
sudo umount /media/WinXP
sudo mount -a
```Now see if the /media/WinXP is more of what you had in mind.

I would use ntfs-3g rather then ntfs.

---

### Post by Morbius1 on 2010-05-25
ntfs is ntfs-3g. There is a link from one to the other.

---

### Post by mikewhatever on 2010-05-25
> **zetharx said:**
> I have found that if I do not put my ntfs partition in fstab, i can mount it simply through the nautilus "places" list.  when i click on the drive to mount and open it, it will automatically mount to /media/VOLUME_LABEL, the directory will be read/writeable, and this can be done without root access.

I would like to be able to auto-mount this drive as described on startup.  No root access, no fstab, just as if i had clicked the drive on "places".  Can anyone help me figure out a way to do so?

Also, as a note, anytime the drive is actually in my fstab with the 'user' option and I try to mount or unmount without root access, I get the following error message.

You haven't specified which drive (or rather partition) you want to mount, nor which version of Ubuntu you run, but the following command should work on all recent versions without root privileges:

```
devkit-disks --mount /dev/sdXY
```
```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```

Can anyone tell me why this doesn't happen when the drive is not in fstab?

You haven't specified which drive (or rather partition) you want to mount, nor which version of Ubuntu you run, but the following command should work on all recent versions without root privileges:

```
devkit-disks --mount /dev/sdXY
```

X is a letter that designates the hard driver (a,b,etc), and Y is a number that designates the partition (1,2,etc).

PS. Last time I checked, ntfs partitions got mounted by default at startup, unless you modified the settings in Nautilus.

---

### Post by zetharx on 2010-05-26
mikewhatever.  thank you.  this is exactly what i was looking for.  i am now mounting from the commandline without the partition being listed in fstab. ^_^

EDIT:
```
udisks --mount /dev/sdXY
```
devkit-disks seems depreciated now.  udisks replaces.  Thanks again.

---

### Post by jasmineaura on 2010-11-23
[http://permalink.gmane.org/gmane.linux.debian.devel.mentors/45363](http://permalink.gmane.org/gmane.linux.debian.devel.mentors/45363)
> udisks --mount has an option --mount-options that can
probably be used to supply options like umask=022. But still, the user
running udisks --mount would need to have plugdev as its login group,
and root obviously doesn't. That alone wouldn't solve the problem of
running udisks-glue as root, either. The mount point is also
determined by udisks, so it's not like I could (or even should) create
it first and assign the right permissions.*sigh*

Having been out of the loop for a while, I did not imagine it would be so complicated to have a custom mount point (different from /media/UUID) without losing non-root/-sudo mount/umount/rw privileges...

As a last resort, I decide to go the setuid ntfs-3g method:
```
# chown root:jas /bin/ntfs-3g
# chmod 4750 /bin/ntfs-3g
# mkdir /mnt/ntfs
```

And added the following line to /etc/fstab
```
/dev/sda1 /mnt/ntfs ntfs-3g rw,user,noauto,exec,windows_names,utf8 0 0
```

and of course, the enumerated "drive" (partition) link in "Places" menu disappears :P

and even better:
```
$ mount /mnt/ntfs
Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at http://ntfs-3g.org/support.html#unprivileged

```

that's just great! lol

so...
```
apt-get source ntfs-3g
```
and.. never mind, it's just not worth it .. :roll:

```
chown root:root /bin/ntfs-3g && chmod 755 /bin/ntfs-3g
```
&& bleh

---

### Post by amjjawad on 2010-11-23
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by jasmineaura on 2010-11-23
> **amjjawad said:**
> [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

ah just what i need, a "graphical fstab editing tool" in python. not :P

```
man fstab
```
```
man mount
```
```
man ntfs-3g
```
```
man udisks
```

---

