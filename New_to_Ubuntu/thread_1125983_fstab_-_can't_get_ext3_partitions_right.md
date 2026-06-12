---
title: "fstab - can't get ext3 partitions right"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Geezle on 2009-04-14
I'm sure there is something really simple that I'm missing here.  I just installed 9.04 Beta on a shiny new drive.  The install went fine, but I can't get rw access on the two storage partitions I made.

Here's my current /etc/fstab after I've been tinkering with it.

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc           proc         defaults                                       0  0  
# / was on /dev/sda1 during installation
UUID=4b22b80c-efc1-4b83-b45c-d67b4ee19a56   /               ext3         relatime,errors=remount-ro                     0  1  
# /home was on /dev/sda6 during installation
UUID=537ae925-1824-4f37-8447-2745b3452734   /home           ext3         relatime                                       0  2  
# /media/sda7 was on /dev/sda7 during installation
UUID=53df4e5f-c486-42f6-a5ed-80b022d67e2e  /media/sda7     ext3         defaults                                      0  2  
# /media/sda8 was on /dev/sda8 during installation
UUID=aa3b5d3f-5ffd-49a1-be8e-5ad0f66db92f  /media/sda8     ext3         defaults                                       0  2  
# swap was on /dev/sda5 during installation
UUID=8dd50ceb-9f0d-49df-b8fa-b9616635a832   none            swap         sw                                             0  0  
/dev/scd0                                   /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                          0  0  
/dev/fd0                                    /media/floppy0  auto         rw,user,noauto,exec,utf8                       0  0  

```
It's /media/sda7 and /media/sda8 that I'm having problems with.  I can mount them, but can't create new files.

Somebody please tell me what I'm missing...I know it's something simple!

Thanks

---

### Post by jbrown96 on 2009-04-14
> **Geezle said:**
> I'm sure there is something really simple that I'm missing here.  I just installed 9.04 Beta on a shiny new drive.  The install went fine, but I can't get rw access on the two storage partitions I made.

Here's my current /etc/fstab after I've been tinkering with it.

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc           proc         defaults                                       0  0  
# / was on /dev/sda1 during installation
UUID=4b22b80c-efc1-4b83-b45c-d67b4ee19a56   /               ext3         relatime,errors=remount-ro                     0  1  
# /home was on /dev/sda6 during installation
UUID=537ae925-1824-4f37-8447-2745b3452734   /home           ext3         relatime                                       0  2  
# /media/sda7 was on /dev/sda7 during installation
UUID=53df4e5f-c486-42f6-a5ed-80b022d67e2e  /media/sda7     ext3         defaults                                      0  2  
# /media/sda8 was on /dev/sda8 during installation
UUID=aa3b5d3f-5ffd-49a1-be8e-5ad0f66db92f  /media/sda8     ext3         defaults                                       0  2  
# swap was on /dev/sda5 during installation
UUID=8dd50ceb-9f0d-49df-b8fa-b9616635a832   none            swap         sw                                             0  0  
/dev/scd0                                   /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                          0  0  
/dev/fd0                                    /media/floppy0  auto         rw,user,noauto,exec,utf8                       0  0  

```
It's /media/sda7 and /media/sda8 that I'm having problems with.  I can mount them, but can't create new files.

Somebody please tell me what I'm missing...I know it's something simple!

Thanks

Probably a permission issue. Check the output of ```
ls -al /media/
``` you should be listed as the owner of each folder (sda7 and sda8). Also make sure that the permissions are at least drw-rw----. The first "rw" means the owner has read and write permissions. You can fix the problem by running ```
sudo chown -R $user:$user /media/sda8 /media/sda7
``` or if its a permission issue ```
sudo chmod 660 /media/sda8 /media/sda7
``` If you have multiple users, and want to give them access as well, use 666 instead of 660.

---

### Post by unutbu on 2009-04-14
Open a terminal (Applications>Accessories>Terminal) and type
```
sudo chown -R $USER:$USER /media/sda{7,8}
```
This will make you (as a normal user) the owner of the /media/sda7 and /media/sda8 directories (and all their subdirectories).

---

### Post by Geezle on 2009-04-15
Thanks guys, I tried both of your suggestions but had no luck.

Can't I just set it up in my fstab file so the drives will auto mount as rw at boot?

---

### Post by unutbu on 2009-04-15
```

UUID=53df4e5f-c486-42f6-a5ed-80b022d67e2e  /media/sda7     ext3         **defaults** 0  2  

```
The mount option "defaults" means **rw**,suid,dev,exec,**auto**,nouser,async. "rw" means the filesystem is getting mounted readable and writeable, and "auto" means the filesystem is getting mounted at boot time. So your /etc/fstab already looks correct.

Could you please post the output of 
```

mount
ls -ld /media/sda7
```

---

### Post by Geezle on 2009-04-18
> **unutbu said:**
> ```

UUID=53df4e5f-c486-42f6-a5ed-80b022d67e2e  /media/sda7     ext3         **defaults** 0  2  

```
The mount option "defaults" means **rw**,suid,dev,exec,**auto**,nouser,async. "rw" means the filesystem is getting mounted readable and writeable, and "auto" means the filesystem is getting mounted at boot time. So your /etc/fstab already looks correct.

Could you please post the output of 
```

mount
ls -ld /media/sda7
```
Okay, now I'm on the trolley.  I thought my fstab looked right, but was convinced something was wrong with it.

Also, sorry about taking so long to get back to this...work's been a little crazy and I haven't had time to even look at the computer recently.

Anyway, here's the output you asked for...

```

jay@jay-desktop:~$ ls -ld /media/sda7
drw-rw---- 2 root root 4096 2009-04-14 13:35 /media/sda7

```

---

### Post by nandemonai on 2009-04-18
> **Geezle said:**
> Okay, now I'm on the trolley.  I thought my fstab looked right, but was convinced something was wrong with it.

Also, sorry about taking so long to get back to this...work's been a little crazy and I haven't had time to even look at the computer recently.

Anyway, here's the output you asked for...

```

jay@jay-desktop:~$ ls -ld /media/sda7
drw-rw---- 2 root root 4096 2009-04-14 13:35 /media/sda7

```

As you can see root owns the mount. Try chown again but use your username instead of $USER.

If you want to make the drive available to others you will then need to modify the permissions appropriately.

---

### Post by Geezle on 2009-04-18
Okay, so I got the ownership changed with chown, but when I rebooted it threw me an error:

```

Log of fsck -C3 -R -A -a 
Sat Apr 18 17:33:14 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda6: clean, 1221/1250928 files, 148048/5000223 blocks
fsck.ext3: Unable to resolve 'UUID=53df4e5f-c486-42f6-a5ed-80b022d67e2e'

fsck.ext3: Unable to resolve 'UUID=aa3b5d3f-5ffd-49a1-be8e-5ad0f66db92f'

fsck died with exit status 8

Sat Apr 18 17:33:15 2009
----------------

```

---

### Post by unutbu on 2009-04-18
Please post the output of

```
sudo blkid -c /dev/null
```

The output will show you the correct UUIDs for sda7 and sda8.
Edit /etc/fstab with the correct UUIDs.

These two UUIDs are apparently not correct:
```
53df4e5f-c486-42f6-a5ed-80b022d67e2e
aa3b5d3f-5ffd-49a1-be8e-5ad0f66db92f
```

---

### Post by Geezle on 2009-04-19
> **unutbu said:**
> Please post the output of

```
sudo blkid -c /dev/null
```

The output will show you the correct UUIDs for sda7 and sda8.
Edit /etc/fstab with the correct UUIDs.

These two UUIDs are apparently not correct:
```
53df4e5f-c486-42f6-a5ed-80b022d67e2e
aa3b5d3f-5ffd-49a1-be8e-5ad0f66db92f
```

I don't know why they were incorrect, but it's all sorted out now.

Thanks to everybody who pitched in with helping me, it's much appreciated! :)

---

