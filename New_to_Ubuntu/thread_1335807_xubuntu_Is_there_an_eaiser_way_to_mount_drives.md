---
title: "xubuntu: Is there an eaiser way to mount drives?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Razmear on 2009-11-23
I switched over to xubuntu a few weeks back and I'm looking for an easier way to get my 80gig secondary drive mounted at start up. 
Used to be able to just see the drive in Places but now I have to go to System -> Disk Utility then select and mount it in there for it to be seen. 
Is there a way to have unmounted drives show in 'places' in xubuntu 
or would it be possible to write a 'batch file' of sorts for the apps or startup menu that would mount the drive and be able to pop up the authorization screen? 

I know I can open a terminal and mount that way too, but I'm looking for for the fewest steps to have my 80gig ntfs mounted after a restart. 

Thanks for any tips,
eb

---

### Post by JairunCaloth on 2009-11-23
You can add it to /etc/fstab

format is:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
```

so for example
/dev/sdb1 /home/me/myotherdrive ext3 defaults 0 2

would mount my second hdd in the directory /home/me/myotherdrive
ext3 is the file-system for the partition
defaults - means accept the default mount options for the filesystem type. You can customize your own options here. Ex.if you wanted it to be readonly you could say 'ro' ect....
dump - honestly no idea.... I've always set to 0
pass - tells fsck the order to check the filesystems. Typically your root filesystem is 1 others are 2.

For more information about supported filesystems and options see man fstab

---

### Post by slumbergod on 2009-11-23
When I set up my other hard drive in this way I had to manually create the mount point first (i.e. what you want to mount it as).

mkdir /media/my_new_drive

---

### Post by JairunCaloth on 2009-11-23
> **slumbergod said:**
> When I set up my other hard drive in this way I had to manually create the mount point first (i.e. what you want to mount it as).

mkdir /media/my_new_drive

Oh yeah, I forgot that very important step. If the directory you want to mount the drive in does not exist, it will fail to mount.

Also once you have added the drive to the fstab, you can run

```
sudo mount -a
```

to test and see if it mounts successfully without rebooting. If it mounts fine with that, you will be good to go, it will always be mounted when you start your computer.

---

