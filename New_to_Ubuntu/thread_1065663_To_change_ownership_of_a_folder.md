---
title: "To change ownership of a folder"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Arthur Millar on 2009-02-10
i followed the advice from this post 
[http://ubuntuforums.org/showthread.php?t=477846](http://ubuntuforums.org/showthread.php?t=477846)

To change ownership of a folder, use
[code]

sudo chown username:users folder

To change ownership of a folder and all of it's contents and subdirectories, use
Code:

sudo chown -R username:users folder

Replace username with your username, and leave users as is (it is the name of the "users" group).[code]

[code]arthur@art-pc:~$ sudo chown -R arthur:arthur /media/Storage/01work[code]
[code]arthur@art-pc:~$ sudo chown -R arthur:users /media/Storage/01work[code]


my terminal did something but it didn't change the ownership of my work01 folder 
so what did i do wrong?

---

### Post by geirha on 2009-02-10
It won't work if the filesystem doesn't handle linux' ownership and permission scheme. If your /media/Storage is FAT or NTFS, then that's why it's not working. You'll need to set the ownership and permissions as mount options in /etc/fstab. Do you have an entry/line for /media/Storage in /etc/fstab?

---

### Post by acidsolution on 2009-02-10
try using 
```

sudo chown -R username:/  folder 


```
always try pressing tab when u start typing username it gives you suggestion .

---

### Post by Toet on 2009-02-10
I never use a : or / so that would be:

```
sudo chown -R username folder
```

---

### Post by Arthur Millar on 2009-02-10
> **geirha said:**
> It won't work if the filesystem doesn't handle linux' ownership and permission scheme. If your /media/Storage is FAT or NTFS, then that's why it's not working. You'll need to set the ownership and permissions as mount options in /etc/fstab. Do you have an entry/line for /media/Storage in /etc/fstab?

on the nose dude spot on
thanks 
no mention of /media/Storage in /etc/fstab
and my storage is set to ntfs so i can plug it into a windows sys if need be.. 
is this necessary?

---

### Post by drs305 on 2009-02-10
> **Arthur Millar said:**
> 

```
arthur@art-pc:~$ sudo chown -R arthur:arthur /media/Storage/**01work**[code]
[code]arthur@art-pc:~$ sudo chown -R arthur:users /media/Storage/**01work**[code]
my terminal did something but it didn't change the ownership of my **work01** folder 
so what did i do wrong?

Not to overstate the obvious, but you did use the correct folder name - whether it is work**01** or **01**work ?

What are the results of:
[CODE]ls -la /media/Storage/**01**work  # or the real folder name
```

---

### Post by geirha on 2009-02-10
> **Arthur Millar said:**
> on the nose dude spot on
thanks 
no mention of /media/Storage in /etc/fstab
and my storage is set to ntfs so i can plug it into a windows sys if need be.. 
is this necessary?

I take it it is an external drive that you plug in via usb/firewire then? Normally when you plug in an external drive with NTFS on, it will be mounted with write access to whomever happens to be logged in at the time. So the two most probable cases is that another user currently has ownership of it. The following should show that:
```
ls -ld /media/storage
```
Or, the filesystem's dirty-bit is set, meaning there are some problems on the filesystem. Ubuntu can't deal with problems on NTFS (the specs are kept secret by microsoft. We're lucky there's even a driver for it), in which case you'll need to plug it into a windows computer and have it run a filesystem check on it. This also happens if you plug it out without unmounting it first.

The following should list all currently mounted filesystem. The line for /media/storage should be useful to see.
```
mount
```

---

### Post by Arthur Millar on 2009-02-10
> **drs305 said:**
> Not to overstate the obvious, but you did use the correct folder name - whether it is work**01** or **01**work ?

What are the results of:
```
ls -la /media/Storage/**01**work  # or the real folder name
```

haha no the real name is definitely 01work
```

arthur@art-pc:~$ ls -la /media/Storage/01work
total 365
drwxrwxrwx 1 root root   4096 2008-10-19 11:43 .
drwxrwxrwx 1 root root  16384 2009-01-25 11:27 ..
-rwxrwxrwx 2 root root  28672 2008-03-04 20:46 adds proposal.xls
-rwxrwxrwx 1 root root 187446 2006-03-08 01:27 adresses.WAB
-rwxrwxrwx 2 root root     83 2006-06-20 14:52 Arthur health24 folder.url
drwxrwxrwx 1 root root   4096 2007-02-05 21:05 arts devient stuff
drwxrwxrwx 1 root root  49152 2009-01-20 14:27 art work
drwxrwxrwx 1 root root   4096 2008-10-19 11:43 dexsktop
drwxrwxrwx 1 root root  65536 2008-03-30 01:24 lauras work
-rwxrwxrwx 1 root root   9216 2006-03-24 10:43 Thumbs.db
arthur@art-pc:~$
```

```
arthur@art-pc:~$ ls -ld /media/storage
ls: cannot access /media/storage: No such file or directory
arthur@art-pc:~$ 
```

thats weird i know it does exist

---

### Post by geirha on 2009-02-10
> **Arthur Millar said:**
> 
```
arthur@art-pc:~$ ls -ld /media/storage
ls: cannot access /media/storage: No such file or directory
arthur@art-pc:~$ 
```

thats weird i know it does exist

It's case sensitive, so /media/Storage/ should work, my bad. However the other ls command showed the permissions, and the permissions that are set means that it should be writable to all users. So, there's something odd here. Could you post the output of mount?

---

### Post by ibuclaw on 2009-02-10
> **Arthur Millar said:**
> haha no the real name is definitely 01work
```
arthur@art-pc:~$ ls -ld /media/storage
ls: cannot access /media/storage: No such file or directory
arthur@art-pc:~$ 
```

thats weird i know it does exist

It does exist :)

Linux is CaSe SeNsiTiVe. So a folder named **storage** is not the same as another folder named **Storage**, if you follow me.

As for the ownership. It looks like it is set at mountpoint.

For this, you'll have to edit your /etc/fstab file to suit the permissions you want.

```
sudo gedit /etc/fstab
```
And find the line that has the 01work filesystem listed and you may see something like this:
> UUID=6AB0419AB0416E1F /media/Storage/01work    ntfs    defaults,nls=utf8 0       1
Well... in the fourth colomn, add the uid= and gid= info, so it now looks like this:
> UUID=6AB0419AB0416E1F /media/Storage/01work    ntfs    defaults,nls=utf8,**uid=1000,gid=100** 0       1
But use the numbers of the user and group that you want assigned.

[edit]
For **your** uid number
```
id -u
```
and for the group number of **users**
```
grep "^users" /etc/group
```
and you'll see something like: **users:x:100:** - the number (100) is the number of that group.

Else, if you want to use **your** group ID number
```
id -g
```
But this tends to be the exact same as the uid number.

Regards
Iain

---

### Post by Arthur Millar on 2009-02-10
```
arthur@art-pc:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/arthur/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=arthur)
/dev/sdc1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
arthur@art-pc:~$

```
```

arthur@art-pc:~$ ls -ld /media/Storage
drwxrwxrwx 1 root root 16384 2009-01-25 11:27 /media/Storage
arthur@art-pc:~$
```
I have a really weird setup 
I tried installing a dual boot on separate drives and now i have a small partition on both drives... sigh i dont know how to configure grub 
but thats for some other time 
been running like this for a year 
2x 80 Gb drives 
1x 160 Gb drives  
storage is an 80Gb  
file system is the 160Gb
and the other one is for games ie gates ;(

thanks for the help but im convinced its the file system 
NTFS

---

