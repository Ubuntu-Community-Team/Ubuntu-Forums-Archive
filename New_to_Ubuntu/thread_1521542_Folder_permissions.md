---
title: "Folder permissions"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by d_darlac on 2010-06-30
I have one partition for all my data, mounted /media/DATA - for not apparent reason (at least to me) the owner changed to root - 
I want to change owner and permissions (I am a total newbie here)
I tried chown, and sudo chown - not working
tried gksudo nautilus, not helping - right click on the folder I am interested, I can choose my name, but a split second later goes back to root..

any ideas (and easy to implement?)

---

### Post by cj.surrusco on 2010-06-30
Are you sure that you are running chown correctly?
In this case it would be:
```
sudo chown username /media/DATA/
```
'username' being your username, of course.

---

### Post by d_darlac on 2010-06-30
I believe I do - 
here is a terminal screen shot
dimitris@dimitris-laptop:~$ cd /media
dimitris@dimitris-laptop:/media$ ls -l
total 20
drwxrwxrwx 1 root root 16384 2010-06-30 10:19 DATA
drwxrwxrwx 1 root root  4096 2010-06-29 22:45 xtra
dimitris@dimitris-laptop:/media$ sudo chown dimitris /media/DATA/
dimitris@dimitris-laptop:/media$ ls -l
total 20
drwxrwxrwx 1 root root 16384 2010-06-30 10:19 DATA
drwxrwxrwx 1 root root  4096 2010-06-29 22:45 xtra
dimitris@dimitris-laptop:/media$

---

### Post by garvinrick4 on 2010-07-01
If you want to give the permission to you.



```
sudo chown -R dimitris:dimitris /media/DATA
```


Use morbius1 in post #10 with fat32 and ntfs

---

### Post by garvinrick4 on 2010-07-01
Be careful using chown and chmod commands.

---

### Post by d_darlac on 2010-07-01
Hi guys, 

tried this Chown syntax too - 
the results are the same:
dimitris@dimitris-laptop:~$ sudo chown -R dimitris:dimitris /media/DATA
[sudo] password for dimitris: 
dimitris@dimitris-laptop:~$ cd /media/DATA
dimitris@dimitris-laptop:/media/DATA$ cd /media
dimitris@dimitris-laptop:/media$ ls -l
total 20
drwxrwxrwx 1 root root 16384 2010-06-30 10:19 DATA
drwxrwxrwx 1 root root  4096 2010-06-29 22:45 xtra

I tried to unmount DATA, but then cannot re-mount it without restarting!
any other ideas?

---

### Post by garvinrick4 on 2010-07-01
I am sorry it did not help you.  I do not have fat32 in fstab (only use chown or chmod in ext)
worked for me. What are you formatted in with DATA? Maybe that is the
angle that we should look into? If you can post back with info or salution if
you would. Right now you have given it chmod a=rwx -R /media/DATA so all have rwx
You just want to change directory and sub directorys to you. Hope someone comes along
to help. What is the format?
Do not use chmod or chown with fat32 or ntfs follow Morbius1 in post's 8,9 and 10. Thank you

---

### Post by Morbius1 on 2010-07-01
Post the output of the following commands please:
```
sudo blkid -c /dev/null
cat /etc/fstab
```My guess is that /media/DATA is a FAT32 or NTFS partition and you have them mounted in fstab. You can't chown or chmod a FAT32 or NTFS formatted filesystem. You can only change ownership and permissions on those filesystems with a mount or in fstab.

---

### Post by d_darlac on 2010-07-01
thanks guys - 
here is the command output - 
dimitris@dimitris-laptop:~$ sudo blkid -c /dev/null
[sudo] password for dimitris: 
/dev/sda1: UUID="e1ddcd57-c436-4a07-a33f-a11efa25c88b" TYPE="ext4" 
/dev/sda2: LABEL="DATA" UUID="70E2C463E2C42EE2" TYPE="ntfs" 
/dev/sda3: LABEL="Swap" UUID="b315130d-bbf5-406a-ad4a-2c3d83f39f0f" TYPE="swap" 
/dev/sda4: LABEL="xtra" UUID="71B2847039501EF8" TYPE="ntfs" 
dimitris@dimitris-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /    ext4    errors=remount-ro    0    1
/dev/sda2    /media/DATA    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf800
/dev/sda4    /media/xtra    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda3    none    swap    sw    0    0

I read on a thread about fstab but not really sure how to use (my first week in Ubuntu...)

---

### Post by Morbius1 on 2010-07-01
In a Terminal type:
```
gksu gedit /etc/fstab
```Change this:
>  /dev/sda2    /media/DATA    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf800To this:
```
 /dev/sda2    /media/DATA    ntfs-3g    defaults,nls=utf8,umask=000,uid=1000 0 0
```Save the file, exit gedit, and back in the terminal type
```
sudo umount /media/DATA
``````
sudo mount -a
```Now see if your data partition is owned by you with read /write access.

---

### Post by d_darlac on 2010-07-01
Thanks Morbius, 

yes now I am the owner - 
where can I find an explanation of what your change did?

thanks again!

---

### Post by Morbius1 on 2010-07-01
The smart @$$ answer is:
```
man mount
```The two important parts in the fstab entry are these:
[B]
umask=000 [/B]
Each digit represents a different type of user:
1st digit = owner
2nd digit = group
3rd digit = everyone else

A 4 turns off read
A 2 turns off write
A 1 turns off execute
A 0 allows full access

[B]uid=1000
[/B]uid is the user id. It's set to you so you can become the owner[COLOR=Blue]
EDIT: Sorry about that. I keep hitting the wrong box when I want to see a preview[/COLOR]

---

### Post by d_darlac on 2010-07-01
Great!
thanks for the detailed response!!!

appreciate it!

---

