---
title: "Lost Home Partition"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by zepl on 2010-01-31
So I went to do a fresh install of ubuntu, and forgot to set my home partition, 
so, I thought I would format it to ext4, so I copied all my files off of it, and put then in the new homefolder of the root partition.
So I went through the install again, and set the home partition, now I'm on the new install and I can't get to my all my old documents.
I know their there, I just got a notifcation of the space almost being full.
I'm just nto sure whats the easiest way to get to them

---

### Post by koenn on 2010-01-31
let's see how you're setup.

run this in a terminal, and post the output here
```
mount
```

---

### Post by zepl on 2010-02-01
I booted with the live cd, and managed to copy most of my stuff back into the new home folder.
but some files and folders say error, access denied, not the owner

and here's the output from mount


> /dev/sda3 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sda2 on /home type ext3 (rw,relatime)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)

---

### Post by zepl on 2010-02-02
I hate bumping threads but I still need help...

---

### Post by ICEB3AR on 2010-02-02
Doesn't it work just to set the owner of the files in your home-folder to your UID GID ?

```
sudo chown -R <your_user_name>:<your_user_group> /home/<your_directory> 
```

Be sure to watch at man page before executing this code.

---

### Post by koenn on 2010-02-02
> **ICEB3AR said:**
> Doesn't it work just to set the owner of the files in your home-folder to your UID GID ?

```
sudo chown -R <your_user_name>:<your_user_group> /home/<your_directory> 
```

Be sure to watch at man page before executing this code.

The problem with this is that it will operate on the *current* home dir - what the op is after, if I understood the OP correctly, is the contents of an old home dir - presumably on /dev/sda3

Isong a live CD is a good approach. 
I suppose it 'll get mounted somewhere in /media, so to reset the permissions, you'd do something like

```
sudo chown -R <your_user_name> /media/path/ 
```
where path is the path to that old home directory

---

### Post by zepl on 2010-02-27
I finally got back to trying this out, but where am I supposed to be logged in to use the above command?
Using the liveCD or the normal boot up.
I tried from the live cd, but I couldnt use my username, so...=/
And when using it from the normal boot up nothing changes, I think it links to the new home partition.
Well, the old home partition doesn't get mounted anywhere, cause its a part of the root system, its in the home folder, but if I'm logged into ubuntu, then the home folder links to the new home partition
and if im in the live cd, half the things say I cant copy then as I dont have permissions, now it wasn't such a big deal before, but now I need those files for my portfolio...for tuesday

---

### Post by koenn on 2010-02-27
you're supposed to do this in a live CD session, but you're right, the chown doesn't make sense, because in a live CD system your user account would not exist. 

in stead, try
```
chmod -R ugo+rw /media/path/
```
where /media/path is that path to your home dir, assuming the live CD session mounted it on /media

---

### Post by zepl on 2010-03-07
After using chown

ubuntu@ubuntu:~$ sudo chown -R eric /media/UbuntuROOT/home/eric/Desktop
chown: invalid user: `eric'

and after  chmod
chmod: changing permissions of `/media/UbuntuROOT/home/eric/Desktop/Documents/Alien.blend': Operation not permitted

This was with the live CD, will try again in a normal session.

---

### Post by koenn on 2010-03-07
well, that's what i said -- the account 'eric' doesn't exist in a Live CD session ...

---

### Post by koenn on 2010-03-07
> **zepl said:**
> 
and after  chmod
chmod: changing permissions of `/media/UbuntuROOT/home/eric/Desktop/Documents/Alien.blend': Operation not permitted

check if it's mounted rw (read+write), and what the current permissions are

---

### Post by zepl on 2010-03-07
Yes, but your suggestion didn't work either so I thought I'd try it out.
Tried it in a normal session, said the path doesnt exist.

---

### Post by koenn on 2010-03-07
> **zepl said:**
> 
Tried it in a normal session, said the path doesnt exist.
because in a normal session, that partition is mounted on /home, not /media. that's your original problem, actually.

you can probably fix this with some mounting back and forth in a normal session, but it's a bit tricky. So let's have one last look at it in a Live CD session. I don't quite understand why you can't just copy those files.

post the output of
```

ls -ld /media/UbuntuROOT/home
ls -ld /media/UbuntuROOT/home/eric

```

---

### Post by zepl on 2010-04-04
So I know its been awhile.
But hopeuflly someone gets back to me

ubuntu@ubuntu:~$ ls -ld /media/UbuntuROOT/home
ls: cannot access /media/UbuntuROOT/home: No such file or directory
ubuntu@ubuntu:~$ ls -ld /media/UbuntuROOT/home/eric
ls: cannot access /media/UbuntuROOT/home/eric: No such file or directory
ubuntu@ubuntu:~$

---

### Post by oldfred on 2010-04-04
This is the guide I used to move /home. Since you have done parts it will be difficult to tell what additional steps you need. 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

The dmrcErrors also has the correct command for permissions and ownership of /home.

---

### Post by zepl on 2010-04-18
Its solved oh its solved.
My blender files are back.
I just had to add sudo to the command from the previous page. Thank you all.

---

