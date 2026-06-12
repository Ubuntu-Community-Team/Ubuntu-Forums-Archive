---
title: "Can not change permission on file of 2nd HD"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by 1flcowboy on 2009-01-21
Cannot change permission or read/write to drive.
I screwed something up trying to do it myself.
help

---

### Post by taurus on 2009-01-21
What filesystem is your second harddrive?  

Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by 1flcowboy on 2009-01-21
Disk /dev/sda: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02b504c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3179    25535286   83  Linux
/dev/sda2            3180        3322     1148647+   5  Extended
/dev/sda5            3180        3322     1148616   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e2899ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081    b  W95 FAT32

---

### Post by 1flcowboy on 2009-01-21
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e4239996-fc8d-499a-bf39-cc8e5974ab86 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2a389877-6853-47d7-8ef4-2cde2bb703f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    
UUID=4976-C43C /media/Ubu2storage   vfat    defaults     0        2

---

### Post by 1flcowboy on 2009-01-21
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              24G   15G  8.7G  63% /
tmpfs                 616M     0  616M   0% /lib/init/rw
varrun                616M  336K  616M   1% /var/run
varlock               616M     0  616M   0% /var/lock
udev                  616M  2.8M  613M   1% /dev
tmpfs                 616M  140K  616M   1% /dev/shm
/dev/sdb1              38G   16K   38G   1% /media/MD1
/dev/sdb1              38G   16K   38G   1% /media/Ubu2storage
/home/marcus/.Private
                       24G   15G  8.7G  63% /home/marcus/Private

---

### Post by 1flcowboy on 2009-01-21
Sorry it took me so long, now on my lunch break,

Help,

c

---

### Post by Michael.Godawski on 2009-01-21
hi,

I guess you mean the fat32 windows drive?

Please post the output of

```
cat /etc/fstab
```

edit: posted while you posted :)

---

### Post by 1flcowboy on 2009-01-21
I did,
thx,

---

### Post by 1flcowboy on 2009-01-21
I'm running out of wits,
Ubuntu is beating me down.

---

### Post by Michael.Godawski on 2009-01-21
open the fstab file with 
```

gksudo gedit /etc/fstab
```and change the line 

```
/dev/sdb1    
UUID=4976-C43C /media/Ubu2storage   vfat    defaults     0        2     
```to
```
 #/dev/sdb1       
         UUID=4976-C43C   /media/Ubu2storage        vfat iocharset=utf8,umask=000     0       2
```save and exit.

remount with

```
sudo mount -a
```

---

### Post by 1flcowboy on 2009-01-21
have tried to do this link several times to no avail.
will not let me have any permissions or change anything on the folder.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I'm lost and so I'm here,

c

---

### Post by Michael.Godawski on 2009-01-21
can you please post the output of 

```
ls -la /media
```

---

### Post by 1flcowboy on 2009-01-21
made changes to fstab,
here is the next thing u asked for,

total 44
drwxr-xr-x  5 marcus users  4096 2009-01-21 06:43 .
drwxr-xr-x 20 root   root   4096 2009-01-21 00:40 ..
lrwxrwxrwx  1 root   root      6 2008-12-18 13:57 cdrom -> cdrom0
drwxrwxrwx  2 root   root   4096 2008-12-18 13:57 cdrom0
-rw-r--r--  1 root   root      0 2009-01-21 00:40 .hal-mtab
drwxr-xr-x  2 root   root  16384 1969-12-31 18:00 MD1
drwxr-xr-x  2 root   root  16384 1969-12-31 18:00 Ubu2storage

do I need to reboot?

c

---

### Post by Michael.Godawski on 2009-01-21
try this too :D

```
  sudo chown -R marcus:marcus /media/Ubu2storage
```

---

### Post by 1flcowboy on 2009-01-21
I had tried that before and got this same answer...

marcus@ubuII:~$ sudo chown -R marcus:marcus /media/Ubu2storage
chown: changing ownership of `/media/Ubu2storage': Operation not permitted

c

---

### Post by cariboo on 2009-01-21
It looks like the from the output of df -h that /dev/sdb1 is mounted twice. you need to edit your fstab;

```
/dev/sdb1
UUID=4976-C43C /media/Ubu2storage vfat defaults 0 2 
```

You need to comment out the line containing /dev/sdb1 eg:

```
#/dev/sdb1
UUID=4976-C43C /media/Ubu2storage vfat defaults 0 2 
```

mounting drives by uuid is the preferred method, so by commenting out the /dev/sdb1 label, it should only mount the drive once.

Once you edit fstab you should be able to unmount /media/MD1

```
sudo umount /media/MD!
```

Once you've unmounted the second instance of /dev/sdb1, you should be able to set read/write permissions on the drive. NOTE: with a vfat drive all you can set is the read/write permissions:

```
sudo chmod -R 777 /media/Ubu2storage
```

Jim

```

```

---

### Post by Michael.Godawski on 2009-01-21
just wanted to add this cariboo907 :)

looked suspicious from the very beginning...

---

### Post by 1flcowboy on 2009-01-21
here is my fstab file again,
I feel so small.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e4239996-fc8d-499a-bf39-cc8e5974ab86 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2a389877-6853-47d7-8ef4-2cde2bb703f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1       
         UUID=4976-C43C   /media/Ubu2storage        vfat iocharset=utf8,umask=000     0

which line do you want me to delete?

c

---

### Post by 1flcowboy on 2009-01-21
and this is what I get..

marcus@ubuII:~$ sudo umount /media/MD!
umount: /media/MD!: not found
marcus@ubuII:~$

---

### Post by Michael.Godawski on 2009-01-21
ok this one is getting tricky...

I would reboot now and see if the fstab change took effect, although the command 
sudo mount -a
should update the fstab entries to the system.

If you say the md partition is not being seen... that's odd because we just checked with the command 

ls -la /media 

that it is there. It is not listed in fstab though.

If after the restart nothing works... we will just mount the partition to a new fresh mount point and see if this will help.

---

### Post by 1flcowboy on 2009-01-21
Darn this thing, I'm rebooting now.

marcus@ubuII:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/4976-C43C does not exist

shoot me,

cowboy

---

### Post by 1flcowboy on 2009-01-21
Rebooting was good thing.
I can see the drive and make a folder.
I am still somewhat confused over what happened.
I now have a "Music1" drive and a "Ubu2storage" folder in my media file browser.
I went Fat32 because I had read it was the easier to share between a Windows system and a Linux?
I can Mount "Music1"
I created a folder called "music" which also shows up in "Ubu2storage"

I want to share this file accross the network to some Windows machine in the house, Question:
Do I share "Ubu2storage" or the "Music1" file?

c

---

### Post by 1flcowboy on 2009-01-21
I also want to add one more drive.
Ur imput would be appreciated, as to file system and mounting procedure.

cowboy

---

### Post by Michael.Godawski on 2009-01-21
I guess one step forward...
You see the content of the fat32 drive and you can create new folders - that is a good thing.

For sharing folder you need samba I guess:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

But I am not an expert myself. So when you feel the mounting issue is solved than create a new thread for the sharing issue. 

If you still have doubts dealing with the fstab thing then ask now :)

Would be good to see the outputs of these commands again after the reboot:

```
cat /etc/fstab
ls -la /media
mount
```

edit:

sure what drive do you want to add?

---

### Post by 1flcowboy on 2009-01-21
marcus@ubuII:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e4239996-fc8d-499a-bf39-cc8e5974ab86 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2a389877-6853-47d7-8ef4-2cde2bb703f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1       
         UUID=4976-C43C   /media/Ubu2storage        vfat iocharset=utf8,umask=000     0 
____________________________________________________________________________

---

### Post by 1flcowboy on 2009-01-21
marcus@ubuII:~$ ls -la /media
total 28
drwxr-xr-x  4 marcus users  4096 2009-01-21 12:22 .
drwxr-xr-x 20 root   root   4096 2009-01-21 12:06 ..
lrwxrwxrwx  1 root   root      6 2008-12-18 13:57 cdrom -> cdrom0
drwxrwxrwx  2 root   root   4096 2008-12-18 13:57 cdrom0
-rw-r--r--  1 root   root      0 2009-01-21 12:06 .hal-mtab
drwxrwxrwx  3 root   root  16384 2009-01-21 12:08 Ubu2storage

---

### Post by 1flcowboy on 2009-01-21
marcus@ubuII:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb1 on /media/Ubu2storage type vfat (rw,iocharset=utf8,umask=000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/marcus/.Private on /home/marcus/Private type ecryptfs (rw,ecryptfs_sig=8f5072940b9ca641,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,user=marcus)
gvfs-fuse-daemon on /home/marcus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marcus)

---

