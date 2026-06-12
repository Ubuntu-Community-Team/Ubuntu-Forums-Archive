---
title: "Copy file from DVD/CD RW Drive to computer"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by anate on 2010-10-14
Hi,
 
I am new to Ubuntu 10.04 server. I am trying to copy a file from DVD/CD RW Drive to the computer using command line. Could you please let me know how to do this.
 
Thanks..

---

### Post by papibe on 2010-10-14
If you have a data formatted CD, just insert it and wait a couple of secs so the drive get auto mounted. Then, you'll need to find out where was mounted. You can use:
```
$ df
```or```
$ mount -l
``` to check for it.

Usually in the desktop version it will be mounted on /media/name, where name is the CD's label.

Is that what you are asking for?

Regards.

---

### Post by anate on 2010-10-14
Thanks for the reply. I entered $ df and I received 
   -root       
    /dev/sda1
 
I couldn't see DVD/CD Rom.

---

### Post by papibe on 2010-10-14
Are you running Ubuntu server?

If the cdrom does not get auto mounted you'll need to do it yourself. First you need to know the name of the device:
```
$ sudo lshw
```
look for the logical names under the *-cdrom category. It'd be something like /dev/cdrom or /dev/sr0. After that, you'll need an empty dir, or better, create one. Then just mount the cdrom:
```
$ mkdir mnt
$ sudo mount /dev/cdrom mnt
```

I hope it helps.

EDIT: you have to sudo your mount.

---

### Post by anate on 2010-10-14
Thanks. I was able to mount the drive. Now how I can copy test.zip file to /home/test folder?
 
I tried the following command but it didn't work.
 
cp mnt/test.zip /home/test/test.zip

---

### Post by oldos2er on 2010-10-14
> **anate said:**
> Thanks. I was able to mount the drive. Now how I can copy test.zip file to /home/test folder?
 
I tried the following command but it didn't work.
 
cp mnt/test.zip /home/test/test.zip

Try ```
cp /mnt/test.zip /home/test
```

---

