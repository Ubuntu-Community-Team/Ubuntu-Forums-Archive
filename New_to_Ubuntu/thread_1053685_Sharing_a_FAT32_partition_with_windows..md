---
title: "Sharing a FAT32 partition with windows."
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Xeoncross on 2009-01-28
Ok, like many people I am trying to setup a couple of partitions from inside Ubnutu.

1:WinXP
2:Shared FAT32
3:Ubuntu

Ok, so that is how my PC looks. I mounted /dev/whatever to /media/disk/ (I think) but now the files are only accessible by "owner" which is my username. Root and groups are locked out which means that my Apache server can't get to the "media/disk/www" directory where I am keeping my shared website files (so I can use them from both Win/linux).

So after reading lots of threads I still am lost as to how to make my /media/disk/ partition accessible by EVERYTHING.

---

### Post by Javich on 2009-01-29
You don't really need to change the mount point, in my opinion you only need to create a symbolic link to the location you want. For example:

Fat32 partition is mounted in /media/windows
the shared "www" folder is in /media/windows/www
Apache is set up to have the "www" folder in /mnt/www 

you type:

```
ln -s /media/windows/www /mnt/www 
```

---

### Post by elvinatom on 2009-01-29
That's kind weird, considering FAT32 is too dumb for permissions.

---

### Post by Xeoncross on 2009-01-29
Ok, thanks for the help.

my drive "dev/sda5" (400GB partition) is now mounted to "media/share/". However, now all the files are locked to root only. My user account "Owner" can't edit them.

I tried to 
```
sudo chmod 777 -R /media/share/
```
But it doesn't seem to do anything. How do I remove all restrictions on this drive as I want it to be shared among WIN/Linux and even the the network
 PC's.

My account shows "419GB Media" and it shows a lock above the folders in there (like "www"). But when I log on as Root I see "share" and the folder is normal. I have tried to use the GUI (as root) to change the group and other permissions but it won't let me.

---

### Post by GepettoBR on 2009-01-29
This is easy, but you'll have to operate under root priviledges, so be careful.

Type this into a terminal: ```
gksudo nautilus
``` This will open a file manager window for the root user. Thhhen, navigate to your disk's mount point, right-click anywhere and selet "Properties". Go to the Permissions tab and set the optins to your liking. Remember to close the window when you're done because it's never a good idea to hae root permissions open for too long.

---

### Post by Xeoncross on 2009-01-29
Ya, I tried that but I get an error that I am not allowed to do that "operation". I can't change the permissions even as root!

Here is what my fstab file looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5b989aa8-773d-4039-a092-fe04751f5432 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5/	/media/share/	auto rw,suid,dev,exec,auto,users,async 0 0

```


Ok, next I tried to CHOWN the media/share/ directory and it gave me the error "Operation not permitted chown: changing ownership".

```
sudo chown -R owner:owner /media/share/
```

---

### Post by GepettoBR on 2009-01-29
> **Xeoncross said:**
> Ya, I tried that but I get an error that I am not allowed to do that "operation". I can't change the permissions even as root!

Here is what my fstab file looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5b989aa8-773d-4039-a092-fe04751f5432 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5/	/media/share/	auto rw,suid,dev,exec,auto,users,async 0 0

```

funny, the "users" switch is present, you should have the correct permissions. I'll do some googling and get back to you.

---

### Post by Gotaro on 2009-01-29
> **Xeoncross said:**
> Ya, I tried that but I get an error that I am not allowed to do that "operation". I can't change the permissions even as root!

Here is what my fstab file looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5b989aa8-773d-4039-a092-fe04751f5432 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5/	/media/share/	auto rw,suid,dev,exec,auto,users,async 0 0

```


Ok, next I tried to CHOWN the media/share/ directory and it gave me the error "Operation not permitted chown: changing ownership".

```
sudo chown -R owner:owner /media/share/
```
This is what worked for me with my shared FAT32 partition:
```
# Shared FAT32 Partition
/dev/sda2 /media/Storage vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```
Hope it's helpful!

---

### Post by Xeoncross on 2009-01-29
Perfect, that worked great! But what is it about that line that is different from what I had? I like that it is fixed - but I would like more to learn from this so I can pass it on. ;)


```

# Shared FAT32 Partition
/dev/sda2 /media/Storage vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

```

```

#Non-working FAT32
/dev/sda5/	/media/share/	auto rw,suid,dev,exec,auto,users,async 0 0

```

---

### Post by jerome1232 on 2009-01-29
With users I believe it just makes it that anyone can mount/umount and the device will be owned by whoever mounted it, since root mounts devices during the bootup process your drive is getting owned by root.

With umask it's setting the permisions on all files/directories to rwxrwxrwx, so it doesn't matter who owns the files everyone has read/write/execute permissions.

You actually don't neet the uid and gid lines in there.

---

### Post by bodhi.zazen on 2009-01-29
> **Xeoncross said:**
> Perfect, that worked great! But what is it about that line that is different from what I had? I like that it is fixed - but I would like more to learn from this so I can pass it on. ;)


```

# Shared FAT32 Partition
/dev/sda2 /media/Storage vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

``````

#Non-working FAT32
/dev/sda5/    /media/share/    auto rw,suid,dev,exec,auto,users,async 0 0

```

The problem you are having is that FAT does NOT support Linux permissions, so they are emulated at the time of mounting.

You specify ownership and permissions at the time of mounting.

umask , dmask, and fmask can give you (limited) options, all files / directories will have the same ownership.

for additional information see :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Gotaro on 2009-01-29
> **Xeoncross said:**
> Perfect, that worked great! But what is it about that line that is different from what I had? I like that it is fixed - but I would like more to learn from this so I can pass it on. ;)


```

# Shared FAT32 Partition
/dev/sda2 /media/Storage vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

```

```

#Non-working FAT32
/dev/sda5/	/media/share/	auto rw,suid,dev,exec,auto,users,async 0 0

```
I think it looks like the replies have got it covered, but here is the one I received explaining the parameters in that line:
[http://ubuntuforums.org/showpost.php?p=6630766&postcount=23](http://ubuntuforums.org/showpost.php?p=6630766&postcount=23)

I have to give credit to HotShotDJ for the line of code!  :)

---

