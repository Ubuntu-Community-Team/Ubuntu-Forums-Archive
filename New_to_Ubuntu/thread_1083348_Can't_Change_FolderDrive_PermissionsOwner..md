---
title: "Can't Change Folder/Drive Permissions/Owner."
date: 2009-02-28
forum: New to Ubuntu
---

### Post by neanderthalman on 2009-02-28
I've run into a problem that I can't seem to find a solution to.  The ubuntu gods will not see fit to allow me to change folder permissions so that users can create/delete files, nor will it allow me to change the folder owner to my user account.  Every thread I've found via search ends with the successful use of chmod or chown....and I'm jealous.  I have yet to find a thread where permissions could not be changed - and if they do exist, they are buried in the thousands of "how do I change permissions" threads.

I have two physical drives, the first is partitioned for windows, ubuntu, and shared data.  The second drive is a single partition.

```

neanderthalman@Humphrey-Ubuntu:~$ sudo blkid
/dev/sda1: UUID="9070C7B070C79AFC" TYPE="ntfs" 
/dev/sda2: UUID="a106cb14-a89d-454d-91c3-4bebb53b52fc" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="2a2cfccd-855a-455f-8f57-ec1e3b3c6187" 
/dev/sda4: UUID="4769-BE65" TYPE="vfat" 
/dev/sdb1: UUID="FA48F91048F8CC7F" LABEL="New Volume" TYPE="ntfs" 

neanderthalman@Humphrey-Ubuntu:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda4 on /media/D type vfat (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/C type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/E type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/neanderthalman/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=neanderthalman)

```

To summarize the configuration:

sda1 is mounted to /media/C and is formatted with NTFS
sda2 is mounted to / and is formatted with EXT3
sda4 is mounted to /media/D and is formatted with FAT32
sdb1 is mounted to /media/E and is formatted with NTFS

Please forgive the lack of creativity in the mount points, it's helped me keep track of what is what.

OK, onto permissions.

The results of ls -la /media are below:
```
neanderthalman@Humphrey-Ubuntu:~$ ls -la /media
total 52
drwxrwxrwx  7 root           root   4096 2009-02-24 07:55 .
drwxr-xr-x 20 root           root   4096 2009-02-15 00:17 ..
drwxr-x---  1 neanderthalman users 16384 2009-02-14 16:17 C
lrwxrwxrwx  1 root           root      6 2009-02-14 20:40 cdrom -> cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom1
drwxr-xr-x  7 root           root  16384 1969-12-31 19:00 D
drwxr-x---  1 neanderthalman users  4096 2009-02-15 14:03 E
-rw-r--r--  1 root           root      0 2009-02-24 07:55 .hal-mtab

```

After which, I have run chmod -v 777 /media/D, then ls -la /media again.  This is the result:
```
neanderthalman@Humphrey-Ubuntu:~$ sudo chmod -v 777 /media/D
mode of `/media/D' changed to 0777 (rwxrwxrwx)

```

Oh, excellent.  Lets check to see the change....

```

neanderthalman@Humphrey-Ubuntu:~$ ls -la /media
total 52
drwxrwxrwx  7 root           root   4096 2009-02-24 07:55 .
drwxr-xr-x 20 root           root   4096 2009-02-15 00:17 ..
drwxr-x---  1 neanderthalman users 16384 2009-02-14 16:17 C
lrwxrwxrwx  1 root           root      6 2009-02-14 20:40 cdrom -> cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom1
drwxr-xr-x  7 root           root  16384 1969-12-31 19:00 D
drwxr-x---  1 neanderthalman users  4096 2009-02-15 14:03 E
-rw-r--r--  1 root           root      0 2009-02-24 07:55 .hal-mtab
neanderthalman@Humphrey-Ubuntu:~$ 

```

And chmod did....nothing.  It lied to me.

Lets try chown.

```
neanderthalman@Humphrey-Ubuntu:~$ sudo chown -v neanderthalman:users /media/D
chown: changing ownership of `/media/D': Operation not permitted
failed to change ownership of `/media/D' to neanderthalman:users
neanderthalman@Humphrey-Ubuntu:~$ 

```

...and chown has *also* failed.  What part of SUDO is the system not understanding!?

In case it's the culprit, and I don't think it is, here's the contents of /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a106cb14-a89d-454d-91c3-4bebb53b52fc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=2a2cfccd-855a-455f-8f57-ec1e3b3c6187 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4    /media/D   vfat    rw,suid,dev,exec,auto,user,async     0        2
/dev/sda1    /media/C   ntfs-3g   auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
/dev/sdb1    /media/E   ntfs-3g   auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```


I've also tried not using octal numbers for chmod, with no success either:
```
neanderthalman@Humphrey-Ubuntu:~$ sudo chmod -v ug=rwx /media/D
mode of `/media/D' changed to 0775 (rwxrwxr-x)
neanderthalman@Humphrey-Ubuntu:~$ ls -la /media
total 52
drwxrwxrwx  7 root           root   4096 2009-02-24 07:55 .
drwxr-xr-x 20 root           root   4096 2009-02-15 00:17 ..
drwxr-x---  1 neanderthalman users 16384 2009-02-14 16:17 C
lrwxrwxrwx  1 root           root      6 2009-02-14 20:40 cdrom -> cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom1
drwxr-xr-x  7 root           root  16384 1969-12-31 19:00 D
drwxr-x---  1 neanderthalman users  4096 2009-02-15 14:03 E
-rw-r--r--  1 root           root      0 2009-02-24 07:55 .hal-mtab

```

and 

```
neanderthalman@Humphrey-Ubuntu:~$ sudo chmod -v ug+rwx /media/D
mode of `/media/D' changed to 0775 (rwxrwxr-x)
neanderthalman@Humphrey-Ubuntu:~$ ls -la /media
total 52
drwxrwxrwx  7 root           root   4096 2009-02-24 07:55 .
drwxr-xr-x 20 root           root   4096 2009-02-15 00:17 ..
drwxr-x---  1 neanderthalman users 16384 2009-02-14 16:17 C
lrwxrwxrwx  1 root           root      6 2009-02-14 20:40 cdrom -> cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom1
drwxr-xr-x  7 root           root  16384 1969-12-31 19:00 D
drwxr-x---  1 neanderthalman users  4096 2009-02-15 14:03 E
-rw-r--r--  1 root           root      0 2009-02-24 07:55 .hal-mtab

```

For kicks, lets try changing permissions for /media/E
```
neanderthalman@Humphrey-Ubuntu:~$ sudo chmod -v ug+rwx /media/D
mode of `/media/D' changed to 0775 (rwxrwxr-x)
neanderthalman@Humphrey-Ubuntu:~$ ls -la /media/D
total 52
drwxrwxrwx  7 root           root   4096 2009-02-24 07:55 .
drwxr-xr-x 20 root           root   4096 2009-02-15 00:17 ..
drwxr-x---  1 neanderthalman users 16384 2009-02-14 16:17 C
lrwxrwxrwx  1 root           root      6 2009-02-14 20:40 cdrom -> cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom0
drwxr-xr-x  2 root           root   4096 2009-02-14 20:40 cdrom1
drwxr-xr-x  7 root           root  16384 1969-12-31 19:00 D
drwxr-x---  1 neanderthalman users  4096 2009-02-15 14:03 E
-rw-r--r--  1 root           root      0 2009-02-24 07:55 .hal-mtab

```

Which also fails.



Can anyone tell me how to convince Ubuntu to change my permissions, and why it's giving me such a hard time?

Also, I know I used 777 and 775 in different areas.  I wanted to see if it changed anything.

---

### Post by Xiong Chiamiov on 2009-02-28
You can try mounting them with the umask=000 option in the fstab.  You'll probably also want to use the -R option (recurse) when chmodding.

---

### Post by neanderthalman on 2009-02-28
> **Xiong Chiamiov said:**
> You can try mounting them with the umask=000 option in the fstab.  You'll probably also want to use the -R option (recurse) when chmodding.

Thanks Xiong,  I've added the umask=000 option, and it gave rwxrwxrwx permissions.

However, chown still will not work, and I don't understand *why* I'm having these difficulties.

Thanks for the advice on the -R option.  I had used it originally....and waited some time for it to do nothing.  I switched to just -v to save time, see what it was doing, and get it working before I used the recurse option and hit up everything.

---

### Post by neanderthalman on 2009-03-01
I've found it!  

[Link](http://ubuntuforums.org/showthread.php?t=225797)

Apparently, FAT32 doesn't support owners or permissions.  However, the permissions can be set when mounting the drive.  In this case the options uid=#### and gid=#### will set the folder owner and the group.

```
/dev/sda4    /media/D   vfat    rw,suid,dev,exec,auto,user,async,umask=000     0        2
```

becomes

```
/dev/sda4    /media/D   vfat    rw,suid,dev,exec,auto,user,async,umask=002,uid=1000,gid=100     0        2 
```

The umask=002 gives 775 permissions, uid=1000 sets the folder owner to my account, and gid=100 sets the group to "users".

You can find your id # by typing id at a terminal, but you can view the id # of any user and group through settings -> administration -> users and groups, and check under the user or group's properties.  It appears that users are numbered starting at 1000, root is 0, and users is 100.

Thanks for pointing me towards fstab settings Xiong!  Will mark as solved.

---

### Post by Xiong Chiamiov on 2009-03-01
I'm glad that you found the answer, especially since I was a bit curious as well.  You can also find the UID and GID of a user a bit faster through the terminal with
```

cat /etc/passwd | grep [username]

```
This will give you something like 
> 
pearson:x:1000:1000::/home/pearson:/bin/bash

where the first 1000 is the UID, and the second is the GID of the primary group.

---

