---
title: "partition doesn't appear in pySDM"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by EntropyReduction on 2010-12-17
I have a problem with /dev/sda3 (an ext4 partition named "Data").

At the moment I impicitly mount the partion (named Data) by choosing
it on the places menu 

I'd like the partition to be mounted at startup,
so I understand I should add it to the fstab table. 

Being a newbie, I intended to use Storage Device Manager (pySDM) 
But sda3 isnt offered as an option, probably because it's already mounted under the name sda3. 

Is i safe to manually add sda3 to fstab?  I guess
something like
/dev/sda8 /media/Data  ext4  relatime  0  0
?

output of "mount"  

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alan)

======================
after selecting "Data" on laces menu as above with following added

/dev/Data on /media/Data type ext4 (rw,nosuid,nodev,uhelper=udisks)

===========================================

output of "ls -l /media"

total 4
drwxr-xr-x 2 root root 4096 2010-12-13 16:43 sda3
 
======================
after selecting "Data"

total 8
drwx------ 10 alan alan 4096 2010-12-15 14:59 Data
drwxr-xr-x  2 root root 4096 2010-12-13 16:43 sda3

===========================================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=9374e917-5dad-4f46-8e95-38c38802755c  /            ext4  errors=remount-ro    0  1
# swap was on /dev/sda6 during installation
UUID=a9fac5c7-6482-426b-a090-4e9344595cdd  none         swap  sw                   0  0

---

### Post by Paddy Landau on 2010-12-17
Yes, you can add it to fstab. **Warning: create a backup of fstab before you do this in case of any serious problems.**

First: Create a directory where you want to mount it. For this example, I'll assume you use dsm in your home directory (replace *entropyreduction* with your user name):
```
mkdir /home/entropyreduction/dsm
```Second: add the following line to your fstab, using the directory you just created:
```
/dev/sda3  /home/entropyreduction/dsm  ext4  defaults  0  2
```If your partition is called DATA, then you could use the following instead:
```
LABEL=DATA  /home/entropyreduction/dsm  ext4  defaults  0  2
```

---

### Post by seawolf167 on 2010-12-17
Click on the fstab link in my sig for a pretty good "fstab how to"

---

### Post by EntropyReduction on 2010-12-20
```
LABEL=DATA  /home/entropyreduction/dsm  ext4  defaults  0  2
```Worked nicely, thanks.

Entirely cosmetic, but it there a way of preventing a shortcut appearing on desktop for that partition?  Don't really need it there, as I now got access via /home.

---

### Post by Paddy Landau on 2010-12-20
> **EntropyReduction said:**
> Worked nicely, thanks.
Excellent. Please mark this thread as solved for someone else looking for this solution.

> **EntropyReduction said:**
> [CODE] Entirely cosmetic, but it there a way of preventing a shortcut appearing on desktop for that partition?
I don't know of any way, but knowing Linux, it must be possible. Have you searched the forums? You might have to start a new thread for this.

---

### Post by oldfred on 2010-12-20
If you mount a partition in /media or /home it will show twice. My workaround was just to mount somewhere else /mnt or just /Data in root and link folders from /Data into  /home.

This may be easier:
Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by Paddy Landau on 2010-12-21
> **oldfred said:**
> If you mount a partition in /media or /home it will show twice.
Curious. I don't have the problem.

---

