---
title: "Another automatic partition mounting question"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by zexoc on 2010-03-13
Hey folks, I asked this question a few years back in this [this]("http://ubuntuforums.org/showthread.php?t=92240") thread, since then I formatted the harddisk, made two partitions - one for windows xp and a second one which is FAT32.

I have since formatted the windows partition and installed Ubuntu in its place and kept the FAT32 one.

My question is: how do I change fstab so that the FAT32 partition mounts automatically ?

_Below is the list from fdisk:_

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ba74ba6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            2046        4998    23719972+   b  W95 FAT32
/dev/sda3            1460        2045     4707045   82  Linux swap / Solaris

(yes its a large swap, I will be running a few applications on it)

_and from fstab:_

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=64ed12a3-351d-45cc-ad46-5c358652e79b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=d83d79ed-5311-4e77-8275-c33eee13d68d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

thanks in advance for any help

---

### Post by garvinrick4 on 2010-03-13
Does sda2 show up under Places drop down menu?

---

### Post by zexoc on 2010-03-13
> **garvinrick4 said:**
> Does sda2 show up under Places drop down menu?

Yes it does - as '24 GB Filesystem'

---

### Post by louieb on 2010-03-13
You add an entry to file **/etc/fstab**
Heres how [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by Jarmen_Deffs on 2010-03-13
Once youve got your fstab line:

UUID=XXXX /mnt/myFatDisk vfat defaults 0 0

you might want to change it to iclude ownership by you and/or permissions for you, eg:

UUID=XXXX /mnt/myFatDisk vfat defaults,uid=1000,umask=022 0 0

---

### Post by zexoc on 2010-03-13
Thanks for the helpful replies, gavin, louie and Jarmen, I have edited the fstab, this is what it is at the moment:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=64ed12a3-351d-45cc-ad46-5c358652e79b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=d83d79ed-5311-4e77-8275-c33eee13d68d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda2       /media/45BB-CAB5   vfat   rw,user,auto,utf8,uid=1000,umask=022     0      2

Does this look correct ? 

How to tell if its not right ?

Thanks again

---

### Post by Jarmen_Deffs on 2010-03-14
> **zexoc said:**
> Thanks for the helpful replies, gavin, louie and Jarmen, I have edited the fstab, this is what it is at the moment:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=64ed12a3-351d-45cc-ad46-5c358652e79b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=d83d79ed-5311-4e77-8275-c33eee13d68d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda2       /media/45BB-CAB5   vfat   rw,user,auto,utf8,uid=1000,umask=022     0      2

Does this look correct ? 

How to tell if its not right ?

Thanks again
I would mount it to a subdirectory of /mnt not /media but that's just my personal preference.  Anything mounted in /media will show up on the desktop.

"defaults" is usually a good start for options, instead of writing out each individual option like that.
You don't have "suid", "exec", "async", or "dev".
"user" won't work with FAT, IIRC, hence the umask and uid.

I suggest just using the options I put in my previous post.

---

### Post by garvinrick4 on 2010-03-14
Make copy of fstab and keep it safe, incase you get it screwed up you have something
to copy and paste to get yourself bootable again with live CD. 

With Live CD:

Remember now with Label you are always /media/your label

sudo mkdir /media/your label    (Need directory to mount)

sudo mount /dev/sda2 /media/your label   (sda2 is whatever yours is)(space after sda2)

sudo umount /media/your label    (umount is right not a typo to unmount)

sudo chroot /media/your label    (gets you as root)

cp /etc/resolve.conf /media/your label/etc/resolv.conf     (gets you internet access wifi)

Once you chroot you will now be in root and do not need sudo:

Practice with Live CD is recommended.

Also you can mount drive or partition in GUI and the use ALT/F2, gksudo nautilus to get into filesytem root. To alter files and save. Be carefull and backup first. Always have a copy of what you are changing.

---

### Post by oldfred on 2010-03-14
Anytime your edit fstab run this. It will remount fstab and if no errors just return or list errors if any.

```
sudo mount -a
```

---

### Post by mkvnmtr on 2010-03-14
On my minimal ubuntu installs I install a package called pmount and things seem to mount automaticaly.

---

### Post by kazakore on 2010-03-14
I just bumped a similar thread in the main section but not for a Live CD. Something I found is that if I edited the fstab and didn't create the directory I was mounting it to it would take up a load of my CPU processes doing nothing. Not sure if this is normal but seemed worth noting. Oldfred also posted in there and was very helpful in there so sure you'll get it sorted.

---

### Post by J V on 2010-03-14
You can just use the devices filename, not the UUID? Cool! 

:)

---

### Post by Morbius1 on 2010-03-14
If you were to use manual partitioning ( or whatever it's called ) during the install process you are given the opportunity to have the fat32 partition automatically mounted at boot. You are asked two questions: how is it formatted and where do you want it mounted. The output looks  like this:

> UUID=C4DB-C1B0  /windows/J      vfat    utf8,umask=007,gid=46 0 2It will by default be owned by root
The umask=007 will allow read / write access to owner (root) and group (gid=46) and no one else.
The gid=46 is the group identifier and it's equal to 46 which is plugdev.
Every local login user is a member of the plugdev group.
So everyone who has a local login username will have read / write access.

The only modification I make to it is to change the UUID to a LABEL, and take possession. I take possession so I can use nautilus-share to share parts or all of that partition to my network.

So I end up with this:

>  LABEL=COMMON  /windows/J      vfat    utf8,umask=007,uid=1000,gid=46 0 2

---

### Post by zexoc on 2010-03-14
Thanks for the help everyone, updated fstab so that it automatically mounts.

Solved

---

