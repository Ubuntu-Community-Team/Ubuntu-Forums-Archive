---
title: "Must enter a password every time I access my shared partition"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by bwsmith7 on 2009-12-08
I've been using Ubuntu 9.1 for the last week and am loving it, but there is one concept I still don't understand - the difference between admin and root priviledges, and how to use root priviledges (besides basic sudo or gksudo commands in Terminal).  

Specifically, I have to enter a password every time I want to access my shared partition.  This causes a big problem with programs such as Picasa, which must re-scan the entire partition every time the program is opened.  Same thing with Banshee.  Is there a way to allow my system to freely access the shared partition?

Here's what I have tried:
Using Nautalus to go to the shared partition, "Storage".  
Opening Properties
Selecting Permissions
Trying to change the folder access for Group and Others

The last step won't work, all my changes are immediately reverted.  First off, is this the right approach? Second, if it is, I assume I need to be a? the? root, so how does that work?

Thanks you all so much for any help, it is greatly appreciated :)

---

### Post by spongypants23 on 2009-12-08
How about adding the partition to /etc/fstab, I think that will cause the partition to mount automatically at boot.

I'm not sure how to work fstab, so  you'll have to get someone to show you..

---

### Post by nothingspecial on 2009-12-08
```
sudo chown -R username:username /path/to/shared/partitions/mountpoint
```

Should do it. Substitute, username for your username. The path to your partition is where it is mounted eg /media/music not /dev/sdb1

---

### Post by JamesParnell on 2009-12-08
What i did, which is probably wrong is this:

```
sudo chown USERNAME /dev/Storage
```then try to change the permissions again.

also try this:

```
sudo gedit /etc/fstab
```and add Storageanother line at the bottom of the list for your partition, this is how i set out my music partition.

```
/dev/sda2 /mnt/music ext4
```where "sda2" is the partition number and "/mnt/music" is the mount point and "ext4" is the filesystem type.*******


this is all probably wrong and there might be a much quicker way to do it if it is right, but it should solve that problem


*******For you this may be along the lines of:
```
/dev/sdaNUMBER /mnt/Storage ext4
```

---

### Post by nothingspecial on 2009-12-08
> **spongypants23 said:**
> How about adding the partition to /etc/fstab, I think that will cause the partition to mount automatically at boot.

I'm not sure how to work fstab, so  you'll have to get someone to show you..

fstab has a lot of options, see [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by bwsmith7 on 2009-12-08
Wow, thanks so much for all the quick responses. I'm not sure I understand them all (I have no idea yet what fstab is, but I'll look it up), but I did try nothingspecial's suggestion:

> **nothingspecial said:**
> ```
sudo chown -R username:username /path/to/shared/partitions/mountpoint
```Should do it. Substitute, username for your username. The path to your partition is where it is mounted eg /media/music not /dev/sdb1

Here's the output from Terminal:

bwsmith@bwsmith-laptop:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bwsmith/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bwsmith)
/dev/sda5 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/Win7 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
bwsmith@bwsmith-laptop:~$ sudo chown -R bwsmith:bwsmith /media/storage
[sudo] password for bwsmith: 
chown: cannot access `/media/storage': No such file or directory
bwsmith@bwsmith-laptop:~$ sudo chown -R bwsmith:bwsmith /media/Storage
bwsmith@bwsmith-laptop:~$ 

I went back to the Storage properties but they appear unchanged, I've attached a screenshot. I'll log out now and log back in and see if Banshee or Picasa can access the files without a password. 

(My apologies if I am way off track - I have no background in computers or programming, so I appreciate your guys' support!)

---

### Post by JamesParnell on 2009-12-08
i never did it that way so i'm lost with that output, would you try the way i suggested?.

---

### Post by bwsmith7 on 2009-12-08
[SIZE=5][COLOR=Lime]**Fixed!**[/COLOR][/SIZE]

[COLOR=Black]It worked! After using the command [/COLOR][FONT=Lucida Sans Unicode][SIZE=1][COLOR=SeaGreen]sudo chown -R bwsmith:bwsmith /media/Storage[/COLOR][/SIZE][/FONT],  [COLOR=Black]I logged back in and started up Banshee and Picasa[/COLOR], and they are reading the files without a password. I can also open my Storage partition without a password:D

Thanks so much for all of your suggestions, its great to have this problem solved. 

([This guy]("http://www.linuxforums.org/forum/ubuntu-help/155816-picasa-loses-watched-folders-prob-cos-access-problem.html") was having the same problem, I'll post the link to this thread for him)

---

### Post by JamesParnell on 2009-12-08
grats.

now i have an easy way to fix it myself for when i buy my new HDD

---

### Post by nothingspecial on 2009-12-08
> **bwsmith7 said:**
> Wow, thanks so much for all the quick responses. I'm not sure I understand them all (I have no idea yet what fstab is, but I'll look it up), but I did try nothingspecial's suggestion:



Here's the output from Terminal:

bwsmith@bwsmith-laptop:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bwsmith/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bwsmith)
/dev/sda5 on [COLOR="Red"]/media/Storage[/COLOR] type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/Win7 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
bwsmith@bwsmith-laptop:~$ sudo chown -R bwsmith:bwsmith [COLOR="Red"]/media/storage[/COLOR]
[sudo] password for bwsmith: 
chown: cannot access `/media/storage': No such file or directory
bwsmith@bwsmith-laptop:~$ sudo chown -R bwsmith:bwsmith /media/Storage
bwsmith@bwsmith-laptop:~$ 

I went back to the Storage properties but they appear unchanged, I've attached a screenshot. I'll log out now and log back in and see if Banshee or Picasa can access the files without a password. 

(My apologies if I am way off track - I have no background in computers or programming, so I appreciate your guys' support!)

First lesson - linux is case sensitive, which I imagine you've just realised. (see the red in the quote)

Second lesson - in general (not always, but 99.9999% of the time, if something works, the shell just returns you to the prompt. That is, your last command didn`t say "wahay, congratulations, you just achieved what you wanted to do" 

error messages = bad
no messages = good

---

### Post by JamesParnell on 2009-12-08
> **nothingspecial said:**
> wahay, congratulations, you just achieved what you wanted to do
Can we make it say that :D

---

### Post by nothingspecial on 2009-12-08
> **JamesParnell said:**
> Can we make it say that :D

Actually, yes.

But I`m not about to start trying.

---

### Post by JamesParnell on 2009-12-08
Aww, what about us simple folk who have to get reassurance from confirmation messages?

---

