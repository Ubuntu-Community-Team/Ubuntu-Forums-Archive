---
title: "urgent: external hard disk permissions trouble"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by kleo skywalker on 2009-04-03
Hello. An external hard disk (Western Digital My Passport) that I wrote data to a few weeks ago is acting weird now. I can't make any changes to the files - rename them or paste new stuff on to the disk - those options are greyed out on the right-click drop-down menu. The owner is another user on this computer who has the same problem, but the group says "Root" and I can't change it: the error message tells me that it's a read-only disk. I need to sort this out asap, so immediate help will be appreciated very very much!
Thanks.
Btw, when I run ```
mount
``` I get ```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/tupush/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tupush)
/dev/sdb1 on /media/My Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

---

### Post by ianhaycox on 2009-04-03
Is it a USB external drive ?

If so I've had this problem where the disk was not properly dismounted previously. Re-mounting didn't help.

My fix was to plug into a Windows box then use the 'Remove safely' option. After that pluging it back into Linux was OK.

Some form of fsck might perform the equivalent operation as the Windows insert/remove function.

---

### Post by kleo skywalker on 2009-04-03
The disk has never been improperly disconnected so far. However, I tried doing that on a Vista box - there was no safely remove option. What do I do now? Please help!

---

### Post by ajgreeny on 2009-04-03
If the windows trick does not work try changing the ownership using nautilus as root (gksudo nautilus) or the terminal (sudo chown -R yourusername:yourgroupname "/media/My Passport")and it may help.  You will need the quote marks in the pathway as there is a space in the folder name.  In future make sure all folders have no spaces but use an underscore instead; it makes life much easier.

I thought the problem of not removing safely in windows only affected NTFS formatted drives not fat as your drive appears to be, and then it was a problem of mounting the drive, not ownership or read-only difficulties.

---

### Post by ianhaycox on 2009-04-03
Sorry never used Vista. Under XP there was a little icon in the task bar which provided the option.

You'll just have to hunt around and try right-clicking stuff.

---

### Post by unikuser on 2009-04-03
There are two things that could have happened. 

1* drive is removed without properly unmounting. Try running filesystem check from terminal.
```
sudo fsck -n /dev/sdb1
sudo fsck /dev/sdb1

```  

2* files/directories are somehow owned by root and you are not able to write to them. change file permissions to your user. 
```
whoami
``` This command will give your user id. 
```
sudo chown -R /dev/sdb1
``` will change all files in /dev/sdb1(your passport drive) to you as owner.

---

### Post by kleo skywalker on 2009-04-03
I really don't know how to use those commands: could you tell me step-by-step? I plug in the disk, open the terminal, and then what do I do?
Thanks, I really need to sort this out asap.

---

### Post by kleo skywalker on 2009-04-03
I tried sudo chown -R /dev/sdb1 and I get chown: missing operand after '/dev/sdb1/'. What does that mean?

---

### Post by MrWES on 2009-04-03
> **kleo skywalker said:**
> I tried sudo chown -R /dev/sdb1 and I get chown: missing operand after '/dev/sdb1/'. What does that mean?

It should be:

```
sudo chown yourusername:yourusername-R /dev/sdb1
```

Also, can you please post the results of:

```
ls -al /media/My\ Passport
```



Bill

---

### Post by kleo skywalker on 2009-04-03
```
sudo chown yourusername:yourusername-R /dev/sdb1
```

Nothing happened.

Also, can you please post the results of:

```
ls -al /media/My\ Passport
```

Here's the output:
```
ls: cannot access /media/My Passport/.Trash-1001: Input/output error
total 7652
drwx------ 13 tinku root   32768 1970-01-01 05:30 .
drwxr-xr-x  5 root  root    4096 2009-04-03 16:46 ..
drwx------  2 tinku root   32768 2009-01-29 13:45 autorun
-r-x------  1 tinku root      54 2008-02-25 10:30 autorun.in_2.org
drwx------ 24 tinku root   32768 2009-01-29 13:45 Documentation
drwx------  6 tinku root   32768 2009-03-12 14:49 Documents
-rwx------  1 tinku root      74 2008-11-06 15:49 Install.ini
-rwx------  1 tinku root   37888 2004-04-24 11:38 JSTART.exe
drwx------  5 tinku root   32768 2008-12-07 13:57 Music
drwx------  8 tinku root   32768 2009-02-22 19:04 Pictures
drwx------  2 tinku root   32768 2009-04-03 06:10 $RECYCLE.BIN
-rwx------  1 tinku root  319488 2008-11-13 12:30 setup.exe
d?????????  ? ?     ?          ?                ? .Trash-1001
drwx------  5 tinku root   32768 2009-03-12 16:15 tupush
drwx------  9 tinku root   32768 2009-03-12 21:25 Videos
-rwx------  1 tinku root      89 2009-04-03 06:07 wdinstaller.log
-rwx------  1 tinku root   42678 2008-11-07 14:56 wdinstaller.xml
-rwx------  1 tinku root 2325721 2008-11-25 11:03 WDSetup.exe
drwx------  3 tinku root   32768 2009-04-03 06:07 WD Sync Data
-rwx------  1 tinku root 4574208 2008-02-08 12:44 WDSync.exe
drwx------  5 tinku root   32768 2009-01-29 13:44 WD_Windows_Tools
```

I have no clue what any of it means. Thanks for helping.

---

### Post by kleo skywalker on 2009-04-06
bump

---

### Post by MrWES on 2009-04-06
> **kleo skywalker said:**
> bump

Try

```
sudo chmod 666 /.local/share/Trash/
```

---

### Post by The Cog on 2009-04-06
I think this is the relevant line from mount:
> /dev/sdb1 on /media/My Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
We see from this that the disk is not ro, it is mounted read-write. So it should be writeable, all other things permitting.

We also see that it is owned by user 1000, which is probably the user who was logged in at the time the disk was plugged in. Use the command **id** to see your current user id to see if it matches. I imagine that user 1000 should be able to write to the disk. I think that disconnecting and reconnecting the drive should make it owned by whoever is logged in at the time it is plugged back in.

We also see that it is vfat not NTFS, so there is no possibility of the problem being that it wasn't unmounted from Windows properly. vfat doesn't have a dirty flag, and anyway, a dirty ntfs drive simply won't mount at all.

So double-check that your current user-id matches the ID that mount says owns the disk. If they match then I'm aftraid I can't think what the problem might be. Have you tried using **gksudo nautilus** and writing to it as root?

---

### Post by kleo skywalker on 2009-04-07
> **The Cog said:**
> I think this is the relevant line from mount:

We see from this that the disk is not ro, it is mounted read-write. So it should be writeable, all other things permitting.

We also see that it is owned by user 1000, which is probably the user who was logged in at the time the disk was plugged in. Use the command **id** to see your current user id to see if it matches. I imagine that user 1000 should be able to write to the disk. I think that disconnecting and reconnecting the drive should make it owned by whoever is logged in at the time it is plugged back in.

We also see that it is vfat not NTFS, so there is no possibility of the problem being that it wasn't unmounted from Windows properly. vfat doesn't have a dirty flag, and anyway, a dirty ntfs drive simply won't mount at all.

So double-check that your current user-id matches the ID that mount says owns the disk. If they match then I'm aftraid I can't think what the problem might be. Have you tried using **gksudo nautilus** and writing to it as root?

Thanks for posting. I have tried writing to the disk from both the users' accounts but it didn't work, gksudo nautilus didn't either.

---

