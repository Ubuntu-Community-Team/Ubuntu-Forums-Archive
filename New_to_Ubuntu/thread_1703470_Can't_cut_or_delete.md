---
title: "Can't cut or delete"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-03-09
I used pysdm so that I could mount the ntfs disk drives at the startup, but now I can't delete (to the trash bin) or cut the contents of disk drives. 

suzuki@suzuki-laptop:~$ ls /dev/disk/by-label -g
total 0
lrwxrwxrwx 1 root 10 2011-03-10 02:17 BackUpFiles -> ../../sda6
lrwxrwxrwx 1 root 10 2011-03-10 02:17 New\x20Volume -> ../../sda5
lrwxrwxrwx 1 root 10 2011-03-10 02:17 System\x20Reserved -> ../../sda1

---

### Post by col48 on 2011-03-09
Permissions problem?

Have the drives - or the bits you want to delete/cut - become owned by root, or maybe have you had your write permission removed?  Can you do anything with these files - rename, copy, even read?

---

### Post by Kirboosy on 2011-03-09
Sounds like a permissions issue. 

Try using this command from a terminal.

```
sudo nautilus
```

Then try to move or delete the file off the drive. If that works then you just need to change permissions on the drives/files.

---

### Post by vanadium on 2011-03-09
Probably you may need to adjust the mounting option in /etc/fstab. Post the output of
```

sudo blkid
cat /etc/fstab

```

---

### Post by RobikShrestha on 2011-03-09
suzuki@suzuki-laptop:~$ sudo blkid
/dev/sda1: UUID="F6582FF7582FB571" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="FA7C40757C402F27" TYPE="ntfs" 
/dev/sda3: UUID="CC983A55983A3DF0" TYPE="ntfs" 
/dev/sda5: UUID="32728DF9728DC1D9" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="0674A5BE74A5B0BB" LABEL="BackUpFiles" TYPE="ntfs" 
/dev/sda7: UUID="9dc8eb36-80b3-4ff0-82f0-4fcad1200fc7" TYPE="ext4" 


suzuki@suzuki-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                         0  0  
# / was on /dev/sda7 during installation
UUID=9dc8eb36-80b3-4ff0-82f0-4fcad1200fc7  /              ext4         errors=remount-ro                0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8            0  0  
/dev/sda6                                  /media/sda6    ntfs         nls=iso8859-1,ro,umask=000,user  0  0  
/dev/sda5                                  /media/sda5    ntfs         nls=iso8859-1,ro,umask=000,user  0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,ro,umask=000,user  0  0  
/dev/sda3                                  /media/sda3    ntfs         nls=iso8859-1,ro,umask=000,user  0  0  



suzuki@suzuki-laptop:~$ sudo nautilus

(nautilus:1882): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:1882): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1882): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1882): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)

(nautilus:1882): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down nautilus-gdu extension
Segmentation fault

---

### Post by QLee on 2011-03-09
Looks to me like you have those drives mounted read only and poster vanadium was correct.

---

### Post by anand warik on 2011-03-09
I recently asked a similar problem

[1700408]("http://ubuntuforums.org/showthread.php?t=1700408")

Although mine wasn't a permission problem as yours the commands suggested to you were similar to mine so here is the reference to the site that might be of value to you as well.
 [fstab]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

---

### Post by RobikShrestha on 2011-03-10
Thanks it worked!

---

