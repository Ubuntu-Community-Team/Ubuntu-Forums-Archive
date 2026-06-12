---
title: "File mount and permition problem"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Digitallad on 2008-12-30
Hi I have a problem that I just cant solve. 
I have a drive that is partitioned into 2 partitions (sg320d1 and sg320d2).They auto mount on boot and if you open sg320d2 for the first time it has read and write privileges but if you open a other drive and then go back to the sg320d2 drive you only have read privileges. Here is what my fstab looks like.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=67a541ce-f727-40b3-a68b-c66240095fdf  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=debd5a0d-09a1-4979-83cc-f6b24d3f076d  none           swap         sw                          0  0  

/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
  
/dev/sdc1                                  /media/500GB   vfat         auto,user,rw,               0  0 

/dev/sdd1                                  /media/SG320D1 vfat         auto,user,rw,               0  0 

/dev/sdd5                                  /media/SG320D2 vfat         auto,user,rw,               0  0   

#usbfs
none                                       /proc/bus/usb  usbfs        devgid=46,devmode=664       0  0  


Hope you point me in the correct direction.

---

### Post by cdtech on 2008-12-30
Have you tried:
```
/dev/sdd1 /media/SG320D1 vfat defaults,umask=007,gid=46 0 0
```
The defaults and umask could give you the user rights your looking for.

---

### Post by Digitallad on 2008-12-30
Nope tried that still the same thing.Fist off it works fine but when I leave the partition and open it again it only have read privileges. I am dumbstruck....

---

### Post by xjcannonx on 2008-12-30
you could try ```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```then paste in this over the current sdd5 line```

/dev/sdd5 /media/SG320D2 vfat iocharset=utf8,umask=000  0    0
```

---

### Post by Digitallad on 2008-12-30
same result.I checked the Ubuntu help site but according it every thing should work. What is strange is that only SG320D2 does it the rest of the drives is ok ....

---

### Post by xjcannonx on 2008-12-30
could this help??> **Digitallad said:**
> Hi I have a problem that I just cant solve. 
I have a drive that is partitioned into 2 partitions (sg320d1 and sg320d2).They auto mount on boot and if you open sg320d2 for the first time it has read and write privileges but if you open a other drive and then go back to the sg320d2 drive you only have read privileges. Here is what my fstab looks like.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=67a541ce-f727-40b3-a68b-c66240095fdf  /              ext3         relatime,errors=remount-rw  0  1  
# /dev/sda5
UUID=debd5a0d-09a1-4979-83cc-f6b24d3f076d  none           swap         sw                          0  0  

/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
  
/dev/sdc1                                  /media/500GB   vfat         auto,user,rw,               0  0 

/dev/sdd1                                  /media/SG320D1 vfat         auto,user,rw,               0  0 

/dev/sdd5                                  /media/SG320D2 vfat         auto,user,rw,               0  0   

#usbfs
none                                       /proc/bus/usb  usbfs        devgid=46,devmode=664       0  0  


Hope you point me in the correct direction.

Maybe add something like ro=remount-rw but just a guess

---

### Post by Michael.Godawski on 2008-12-30
hi, 
can you please post the output of:
```

ls /dev/disk/by-uuid/ -alh
```

---

### Post by Digitallad on 2008-12-31
Hi sorry I was out of office for the day here is the out put:

paul@ubuntu8:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 180 2008-12-31 08:48 .
drwxr-xr-x 6 root root 120 2008-12-31 08:48 ..
lrwxrwxrwx 1 root root  10 2008-12-31 08:48 48E4-873F -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-12-31 08:48 67a541ce-f727-40b3-a68b-c66240095fdf -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-12-31 08:48 70e3f456-918f-43c5-9ba1-d443fe504bdb -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-12-31 08:48 9091-CADA -> ../../sdd1
lrwxrwxrwx 1 root root  10 2008-12-31 08:48 D8DA-B04D -> ../../sdd5
lrwxrwxrwx 1 root root  10 2008-12-31 08:48 debd5a0d-09a1-4979-83cc-f6b24d3f076d -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-12-31 08:48 ec4a9580-691b-47c4-9ede-caf69c28e357 -> ../../sda1

---

### Post by Digitallad on 2008-12-31
You are write it didn't work.It actually broke my login screen but I just had to go back to my backup and all was ok again but still the same problem.. Regarding the post by xjcannonx

---

### Post by cdtech on 2008-12-31
Showing the output of:
```
sudo fdisk -l
```
could help identify the disk filesystem. Also the permissions set within the /media directory:
```
ls -la /media
```

---

### Post by Digitallad on 2009-01-01
> **cdtech said:**
> Showing the output of:
```
sudo fdisk -l
```
could help identify the disk filesystem. Also the permissions set within the /media directory:
```
ls -la /media
```
Hello here is the out puts 

> paul@ubuntu8:~$ sudo fdisk -l
[sudo] password for paul: 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x603b603b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aefc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    b  W95 FAT32

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f9664b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       25063   201318516    c  W95 FAT32 (LBA)
/dev/sdd2           25064       38913   111250125    f  W95 Ext'd (LBA)
/dev/sdd5           25064       38913   111250093+   b  W95 FAT32



And

> paul@ubuntu8:~$ ls -la /media
total 116
drwxr-xr-x  12 root root     4096 2008-12-31 17:49 .
drwxr-xr-x  21 root root     4096 2008-12-21 22:48 ..
drwxrwx---  14 root plugdev 16384 1970-01-01 02:00 500GB
lrwxrwxrwx   1 root root        6 2008-12-21 09:35 cdrom -> cdrom0
drwxr-xr-x   2 root root     4096 2008-12-21 09:35 cdrom0
-rw-r--r--   1 root root        0 2008-12-31 17:49 .hal-mtab
drwxr-xr-x   2 root root     4096 2008-12-21 17:05 sdb1
drwxr-xr-x   2 root root     4096 2008-12-21 16:55 sdb5
drwxr-xr-x   2 root root     4096 2008-12-21 16:55 sdc1
drwxr-xr-x   2 root root     4096 2008-12-21 17:05 sdd1
drwxr-xr-x   2 root root     4096 2008-12-21 17:05 sdd5
drwxrwx---  17 root plugdev 32768 1970-01-01 02:00 SG320D1
drwxrwxrwx 118 root root    32768 1970-01-01 02:00 SG320D2
drwxr-xr-x   2 root root     4096 2008-12-21 17:05 Test1


I saw it the 2nd command that SG320D2 and the Cd ROM was a different color..

---

### Post by Digitallad on 2009-01-06
I made mistake with my previous description of my problem.The drive is in permanent write only regardless of what I do to the fstab Can any help me?

---

### Post by Digitallad on 2009-01-07
Is there any one that could help me?

---

