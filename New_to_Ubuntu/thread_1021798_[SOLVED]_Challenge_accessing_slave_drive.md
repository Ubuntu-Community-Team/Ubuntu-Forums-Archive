---
title: "[SOLVED] Challenge accessing slave drive"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by seawind24 on 2008-12-25
Hi all

During the last week I have installed Ubuntu on an older PC for trial prior to installing it on my main MS unit. Have been very impressed so far but have been stumped about how to access a slave drive. I have spent hours on this forum and while I have picked up a lot, I now need an expert's help.

Specifically the slave shows in Places as 20.0 GB Media. If I select it the only file there is lost+found. If I create a document, docs, in Open Office and try to save it to the slave I get "Error saving the document docs /media/disk/docs.odt does not exist." After OK another error message "Error saving the document docs: General input/output error".

Further, if I try, in su mode, to create a directory "docs" in dev/media/disk, I get the response "cannot create directory "docs" : permission denied".

Following is a screen dump of responses which may help you =

charles@charles-desktop:~$ sudo fdisk -l
[sudo] password for charles:

Disk /dev/sda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed00ed00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1744    14008648+  83  Linux
/dev/sda2            1745        1826      658665    5  Extended
/dev/sda5            1745        1826      658633+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8f0f8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+  83  Linux


charles@charles-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=789f81b9-7b60-48be-a7b0-a161f8f75080 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=825d603f-8e5a-4626-ac06-c50a85c6e2ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1/media/disk ext3 auto,user,rw,uid=1000,gid=1000 0 0


charles@charles-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              14G  2.6G   10G  21% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  100K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.7M  249M   2% /dev
tmpfs                 252M  184K  251M   1% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1              19G   44M   18G   1% /media/disk
charles@charles-desktop:~$

I am returning to Unix after 15 years so any assistance would be appreciated!

Cheers
Charles

---

### Post by ercferret18 on 2008-12-25
try going to a terminal, changing directory to the drive, and then enter "touch docs"

---

### Post by ZhiZaki on 2008-12-26
Ya know, it sounds like a permissions issue to me. Try `chmod -r 777 /mount/point` or `chown -R username.usergroup /mount/point`. Had similar issues with hard drives I didn't mount during the install.

---

### Post by bodhi.zazen on 2008-12-26
It does not sound like a permissions problem to me as it failed as root.

The only problem I see is in your fstab entry :

> [COLOR=red]/dev/sda1/media/disk[/COLOR] ext3 auto,user,rw,uid=1000,gid=1000 0 0I think that line should read :

```
/dev/[COLOR=navy]**sdb1**[/COLOR] /media/disk ext3 auto,user 0 0
```I would unmount /media/disk, make the change to fstab, and in this case, reboot.

you set the permissions of linux permissions with chown and chmod 

so, with the partition mounted :

```
sudo chown user.user /media/disk
sudo chmod 770 /media/disk
```

where "user" == your log in name. No need to use -R with those commands as the disk is currently empty.

---

### Post by seawind24 on 2008-12-26
Thanks for the advice bodhi. I assume that there is no space between sdb1 and /media. I have edited that file now. Using the chown command, I assume that in place of user.user I put charles.charles , charles being my login name. If so, it returns the error "change of ownership not permitted". When I try to chmod,  the response is "operation not permitted". I assume that the chmod will not work if the chown fails.
Charles

Ps Just got it going by only putting charles in once in the chown command.
Many thanks for your valuable advice.

---

### Post by bodhi.zazen on 2008-12-26
yes, you need a space between /dev/sdb1 and /media/disk

---

