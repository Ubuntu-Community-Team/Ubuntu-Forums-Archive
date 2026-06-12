---
title: "Way to mount drive?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by furiousjason on 2010-08-23
What I am looking to do is have my windows partition mount when starting Ubuntu. Reason why is I have my Firefox profile to use in both windows 7 and Ubuntu. If I don't first mount the drive after logging on Firefox errors when opening unless I first connect to the windows partition.

---

### Post by Matt__ on 2010-08-23
```
sudo apt-get install ntfs-config
```

allow write permsission at prompt

---

### Post by furiousjason on 2010-08-23
I ran that command and rebooted. The filesystem does not mount. I can go to places and click on it and it mounts and then I can open Firefox without a problem.

---

### Post by Confucius! on 2010-08-23
You need to add it to your /etc/fstab to get it to mount automaticly with you start Ubuntu.

---

### Post by Morbius1 on 2010-08-23
Post the output of the following commands and tell us which partitions you want to automount:

```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

### Post by furiousjason on 2010-08-23
> **Morbius1 said:**
> Post the output of the following commands and tell us which partitions you want to automount:

```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```


/dev/sda1: LABEL="System Reserved" UUID="8C5CB3005CB2E45C" TYPE="ntfs" 
/dev/sda2: UUID="388CB70C8CB6C422" TYPE="ntfs" 
/dev/sda3: UUID="869d4082-8e14-4367-be01-91f75a1cf53e" TYPE="ext4" 
/dev/sda4: LABEL="Storage" UUID="42F57C562F217C73" TYPE="ntfs" 


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=869d4082-8e14-4367-be01-91f75a1cf53e /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I am wanting the sda2 mounted.

---

### Post by Morbius1 on 2010-08-23
What I would do is this:

Create a mount point for the sda2 partition:
```
sudo mkdir /mnt/Win7
```Edit fstab as root:
```
gksu gedit /etc/fstab
```Add the following line to the end of fstab:
```
 /dev/sda2 /mnt/Win7 ntfs defaults,nls=utf8,umask=000 0 0
```Save the fstab file, and back in the terminal:
```
sudo mount -a
```If there are any errors after issuing that last command post them. If not then you should be able to access the Win7 partition at /mnt/Win7

Something is odd about your fstab - you have no swap - curious.

---

### Post by furiousjason on 2010-08-23
I followed those steps. Once I rebooted now I do not see the drive and cannot even manually access it.

---

### Post by Morbius1 on 2010-08-23
What is the output of the following command:
```
mount
```

---

### Post by furiousjason on 2010-08-23
> **Morbius1 said:**
> What is the output of the following command:
```
mount
```

/dev/sda3 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
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
/dev/sda4 on /media/Storage_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/System Reserved type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/Win7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jason/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jason)

---

### Post by Morbius1 on 2010-08-23
It's right where you told it to mount:
>  /dev/sda2 on [COLOR=Blue]/mnt/Win7[/COLOR] type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

---

### Post by furiousjason on 2010-08-23
> **Morbius1 said:**
> It's right where you told it to mount:

Great! Just needed to recreate the Firefox profile. Sorry for the ignorance. Just switch to Ubuntu and still learning. Thanks for your help!

---

### Post by Morbius1 on 2010-08-23
I guess in retrospect I should have made the mountpoint in /media. That way it would have produced a mount icon on the desktop. But in my defense I did say " What I would do" :)

I don't like to clutter my desktop so I put mount points in /mnt. Mountpoints in /media or /home/user_name produce desktop icons, if they're in /mnt they do not.

---

### Post by furiousjason on 2010-08-23
I'm with you I hate clutter on my desktop. If I would of read the command a little more closely I should of figured it out. And I don't need to access that drive except for my Firefox profile so if I HAVE to use windows I can have the same profile. So you actually did exactly what I wanted. Thanks again.

---

