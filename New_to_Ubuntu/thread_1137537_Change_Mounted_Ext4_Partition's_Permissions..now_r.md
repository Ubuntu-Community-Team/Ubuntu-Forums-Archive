---
title: "Change Mounted Ext4 Partition's Permissions..now root"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by contax on 2009-04-25
I just put together new hardware and loaded 9.04 Server(64).  I created a few partitions that I want to use for data storage.  I did not place, nor want this data in my home partition.

I have searched and just confused myself.  I would like to change permissions for these data partitions, but after searching I'm just confused.  Presently root owns the partitions.

I tried to change the permission of the new partition to my sign on user name using this command in terminal:

sudo chown -R myusername /nameofpartiton

This did not work.  Please set me straight... thanks

---

### Post by logos34 on 2009-04-25
permissions and ownership are two different things.

try

sudo chmod -R 755 /partition/mountpoint

and/or

sudo chown -R username:username /partition/mountpoint

---

### Post by adult swim on 2009-04-25
try chowning the location where the partitions are mounted to ie
 chown -R username:username /media/disk

---

### Post by contax on 2009-04-25
> 
try

sudo chmod -R 755 /partition/mountpoint

and/or

sudo chown -R username:username /partition/mountpoint

I think that part of my problem is understanding what  "/partition/mountpoint" is.

How do I determine "mountpoint"?

Thanks..

---

### Post by adult swim on 2009-04-25
make sure the partition is mounted and then go to a terminal and and enter in ```
mount
```that will return a list of things and where they are mounted to.  ive got a thumb drive in my computer that shows up as ```
/dev/sdb1 on /media/FEDORA
``` that means my drive /dev/sdb1 is mounted to the location of /media/FEDORA

---

### Post by logos34 on 2009-04-25
i.e. wherever the partition is mounting

the

> mount

command will show

---

### Post by contax on 2009-04-25
OK.. I don't seem to be selecting the right name.. here is what I get with the command "mount":

/dev/mapper/San--Leandro--Backup--Volume--Group-Root--Logical--Volume on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-server/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext2 (rw,relatime)
/dev/mapper/San--Leandro--Backup--Volume--Group-Home--Logical--Volume--Name on /home type ext4 (rw,relatime)
/dev/mapper/San--Leandro--Backup--Volume--Group-Other--Program--Logical--Volume on /opt type ext4 (rw,relatime)
/dev/mapper/San--Leandro--Backup--Volume--Group-Back--Office--Logical--Volume on /svr-back-office-san-leandro type ext4 (rw,relatime)
/dev/mapper/San--Leandro--Backup--Volume--Group-Front--Office--Logical--Volume on /svr-front-office-san-leandro type ext4 (rw,relatime)
/dev/mapper/San--Leandro--Backup--Volume--Group-Instrument--Logical--Volume on /svr-instrument-san-leandro type ext4 (rw,relatime)
/dev/mapper/San--Leandro--Backup--Volume--Group-temporary--logical--volume on /tmp type ext4 (rw,relatime)
/dev/mapper/San--Leandro--Backup--Volume--Group-User--Local--Logical--Volume on /usr type ext4 (rw,relatime)
/dev/mapper/San--Leandro--Backup--Volume--Group-Variable--Logical--Volume on /var type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

so for my partition /svr-back-office-san-leandro, would the mount point be:
/dev/mapper/San--Leandro--Backup--Volume--Group-Back--Office--Logical--Volume

Here is what I used:

sudo chown -R gary:gary /svr-back-office-san-leandro/dev/mapper/San--Leandro--Backup--Volume--Group-Back--Office--Logical--Volume

gary is my user name

What I get is:
"no such file or directory"
I must be using the wrong mount point designation.

---

### Post by adult swim on 2009-04-25
does it work when you try ```
sudo chown -R gary:gary /svr-back-office-san-leandro
```

---

### Post by contax on 2009-04-25
does it work when you try
Code:
sudo chown -R gary:gary /svr-back-office-san-leandro

Wow, it does work.

What is really strange is that this is where I started after following another post that I searched on, but I must have had a typo and then dismissed the approach.

Thanks..

---

### Post by Martynf_uk on 2010-11-08
:) I'm a newcomer to Ububtu and just love finding old posts like this that help me over obstacles. I also created two new partitions on a new drive and couldn't figure out why it wouldn't let me create directories.

---

### Post by bemental on 2011-03-22
> **Martynf_uk said:**
> :) I'm a newcomer to Ububtu and just love finding old posts like this that help me over obstacles. I also created two new partitions on a new drive and couldn't figure out why it wouldn't let me create directories.

Same here, this post worked like a charm!

It's always funny how when you Google an issue you're having (site:.ubuntuforums.org) you find posts that were started years ago that are still relevant.


Keep up up everyone!

---

