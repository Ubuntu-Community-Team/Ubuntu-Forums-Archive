---
title: "help with chmod"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-03-07
I changing the permissions on a map that has sub maps, problem is that only the map that I change permission get changed and not those below.

```

ls -l
Folder A = drwx-wx-wx
chmod go-wx Folder A
ls -l
Folder A = drwx------
cd Folder A
ls -l
Folder A.a = drwx-wx-wx
Folder A.b = drwx-wx-wx

```
question should home folder have something like this drwxr-xr-x?

Other problem I got is that I recently created a new partition that I don't have permission to, I would like to change this for the entire partition so I become the owner, yet I would like to keep 'lost+found' as it's.

Last thing should I be worried about this?
```

:/$ ls -l
totalt 92
drwxr-xr-x   2 root root  4096 2009-03-04 01:23 bin
drwxr-xr-x   3 root root  4096 2009-03-04 21:25 boot
lrwxrwxrwx   1 root root    11 2009-03-04 00:22 cdrom -> media/cdrom
drwxr-xr-x  16 root root 14760 2009-03-07 17:53 dev
drwxr-xr-x 124 root root 12288 2009-03-07 17:53 etc
drwxr-xr-x   4 root root  4096 2009-03-04 00:29 home
lrwxrwxrwx   1 root root    33 2009-03-04 01:27 initrd.img -> boot/initrd.img-2.6.27-11-generic
drwxr-xr-x  15 root root 12288 2009-03-04 01:33 lib
drwxr-xr-x   4 root root  4096 2009-03-04 01:33 lib32
lrwxrwxrwx   1 root root     4 2009-03-04 00:23 lib64 -> /lib
drwx------   2 root root 16384 2009-03-04 00:16 lost+found
drwxr-xr-x   7 root root  4096 2009-03-07 17:53 media
drwxr-xr-x   2 root root  4096 2008-10-20 14:27 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 22:04 opt
dr-xr-xr-x 152 root root     0 2009-03-07 18:51 proc
drwxr-xr-x  14 root root  4096 2009-03-04 01:22 root
drwxr-xr-x   2 root root  4096 2009-03-04 01:23 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 22:04 srv
drwxr-xr-x  12 root root     0 2009-03-07 18:51 sys
drwxrwxrwt  11 root root  4096 2009-03-07 17:53 tmp
drwxr-xr-x  12 root root  4096 2009-03-04 00:53 usr
drwxr-xr-x  15 root root  4096 2008-10-29 22:28 var
lrwxrwxrwx   1 root root    30 2009-03-04 01:27 vmlinuz -> boot/vmlinuz-2.6.27-11-generic

```

---

### Post by taurus on 2009-03-07
You can run chmod with the -R (recursive) to have everything under the directory (files & subdirectories to have the same permissions).

```
chmod -R 766 directory_name
```

---

### Post by SpinningAround on 2009-03-07
> **taurus said:**
> You can run chmod with the -R (recursive) to have everything under the directory (files & subdirectories to have the same permissions).

```
chmod -R 766 directory_name
```

Thanks work like a charm :) question what does the 'd' stand for in drwxr--r-- ?


I think I figured out how to edit paritions but something I don't get is why they are different 10 vs 3 or what 4096 stand for?

```

:/media$ ls -l
drwxr--r-- 10 linux linux 4096 2009-03-07 18:50 Storage
drwxr--r--  3 linux linux 4096 2009-03-07 17:34 Storage2

```

---

### Post by taurus on 2009-03-07
The d in front means directory.  The l means link and if it's **[COLOR="Blue"]_[/COLOR]**rwxr_xr_x, then it means a file.

---

### Post by malibusurfer2 on 2009-05-07
Ubuntu 9.04. oops I typed sudo chmod 666 / in a terminal window. Now I can't boot into Ubuntu.  Any way out? Or, do I have to reinstall?

Thanks for any help.

---

### Post by malibusurfer2 on 2009-05-07
pmg had this suggestion. Would it work? Could someone be more specific?

How do you mount / in /mnt?
How do you sync?

 Re: sudo chmod 666 /
I think you should be able to boot your install cd, mount your root partition in some other location (e.g. /mnt) and then chmod it back (e.g. chmod 755 /mnt) then "sync" to be sure it writes the update to the drive.

Sorry for the Newbee questions, but unlike Windows, I have been able to just use Ubuntu without worrying too much about what is under the hood.

Thanks

---

### Post by Tom Mann on 2009-05-07
You do have potential to repair the file system permissions, but you'll probably need a live cd to do it:

- boot the cd in live mode
- fire up a terminal

type:

```
sudo fdisk -l
```

Check the output to find your linux partition (It *should* be the first Linux entry in the last column. Note the partition name (/dev/sd...) at the start of the line.

```
sudo mount /dev/sdXn /mnt
```where sdXn is the partition name you noted earlier.

now typing```
ls /mnt
```should give you a listing of directories, including bin, etc, sbin, home, tmp and so on.

If it does not do a ```
sudo umount /mnt
```then repeat the steps above moving to the next Linux partition.

I don't know the chmod value at the moment (I'm not at my PC :() but if anyone knows the mask for the file system maybe they can help here?

EDIT: Command seems to be:```
sudo chmod -hRv 755 /mnt
```

---

