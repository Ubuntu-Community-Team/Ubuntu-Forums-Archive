---
title: "external hard drive now 'read only', sudo nautilus doesnt help."
date: 2009-12-03
forum: New to Ubuntu
---

### Post by phantomjoker on 2009-12-03
I try and be as descriptive as possible with my titles so it speaks for itself...

but basically i recently pluged in my mobile to put some more files on it and got the error it was 'read only' so i tried changing the permissions by opening sudo nautilus and going to the properties but it told me i couldnt.

I unpluged the mobile, and retired a minute later - 1 file transfered then the same error. 

I read on a similar thread someone mentioning using a live cd, but they didnt go into much detail so im not sure what to do once booted into live.

Is there a way to get my permissions back?

thanks forum

---

### Post by bsharp on 2009-12-03
Please post the output of
```
mount
```

I'm thinking the way it is mounted may be read-only, which would prevent ANY write io to that device.

---

### Post by phantomjoker on 2009-12-03
> home:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw,relatime)
/dev/sda8 on /media/680gb type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mckenzie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mckenzie)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=mckenzie)
/dev/sdb on /media/Memory card type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


Note - im pretty sure its '/media/Memory card'

---

### Post by M!K3_$ on 2009-12-03
maybe just a simple chmod

---

### Post by phantomjoker on 2009-12-03
please expand? last time i used chmod i completely re-wrote every permission on my system and totally destroyed it. I think i need some instructon

cheers

---

### Post by M!K3_$ on 2009-12-03
> **phantomjoker said:**
> /dev/sdb on /media/Memory card type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1 000,utf8,umask=077,flush) 
from the output of that line of the mount command it looks like it should be read/write
> rw

you could try remounting it with the
```
sudo mount -w /dev/sdb /media/Memory card
```

---

### Post by M!K3_$ on 2009-12-03
> **phantomjoker said:**
> please expand? last time i used chmod i completely re-wrote every permission on my system and totally destroyed it. I think i need some instructon

cheers

hehe, did you do 
```
sudo chmod 777 -R /
```

---

### Post by phantomjoker on 2009-12-03
> home:~$ mount -w /dev/sdb /media/Memory card
mount: only root can do that
home:~$ sudo mount -w /dev/sdb /media/Memory card
[sudo] password for mckenzie: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


didnt quite work, i dont think -w is a command

---

### Post by phantomjoker on 2009-12-03
no, i think it was just sudo chmod /* or something equally as hideous.

Dont do it, its not pretty.

---

### Post by phantomjoker on 2009-12-03
my mistake, it was the chown command and i changed all permissions on my entire system to USER.... great fun

---

### Post by M!K3_$ on 2009-12-03
> **phantomjoker said:**
> didnt quite work, i dont think -w is a command

[http://linux.die.net/man/8/mount]("http://linux.die.net/man/8/mount")

it should be.

```
sudo mount -o rw /dev/sdb /media/Memory card
```

that should be the same.

---

### Post by M!K3_$ on 2009-12-03
it should really mount read/write by default though.

---

### Post by phantomjoker on 2009-12-03
Unfortunatly i get the same message again. thanks for your help so far, by the way.

>  sudo mount -o rw /dev/sdb /media/Memory card
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


---

### Post by M!K3_$ on 2009-12-03
no problem. lets see if we cant figure this out.

lol, just had an idea. you have to unmount it first.
you can do that by right-clicking on the drive and clicking unmount
or by
```
sudu umount /dev/sdb
```

then maybe just try the default mount again
```
sudo mount /dev/sdb /media/Memory card
```

---

### Post by phantomjoker on 2009-12-03
> $ sudo umount /dev/sdb
$ sudo mount /dev/sdb /media/Memory card
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
$ sudo mount /dev/sdb
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab


didnt work again, tried something but that didnt work either

---

### Post by M!K3_$ on 2009-12-03
that just means the mount syntax is wrong. perhaps the directory structure is wrong. double check everything.

---

### Post by Some Penguin on 2009-12-03
> **phantomjoker said:**
> didnt work again, tried something but that didnt work either

Try mounting a partition, not the whole device.  Also, "Memory device" has a space in it.  Try quotes.

---

### Post by M!K3_$ on 2009-12-03
```
sudo mount -t vfat /dev/sdb /media/Memory card
```
try that i guess. i'm starting to run out of ideas.
lol, maybe try unplugging it and plugging it back in

---

### Post by Some Penguin on 2009-12-03
> **phantomjoker said:**
> my mistake, it was the chown command and i changed all permissions on my entire system to USER.... great fun

chown changes ownership.
chmod changes permission.

What command *did* you do?  Without knowing that, it might be difficult to know how to undo it.  It might be difficult anyway, but...

('chown -R foo.bar /' would make every file owned by user foo, group bar -- provided that the one doing chown had permission to do so.  
 'chmod og-rwx /' would remove all read/write/execute permissions from everybody *except* the owner of the file.)

And so forth.

I see nothing in the mount() output that suggests that your problem is the fs being mounted ro; indeed, the mount in /media/Memory\ card is rw.  So that is *not* the problem, unless you're trying to write to the CD, which is ro.  Instead, presumably you've removed your local permissions, or the drive is full (and full tends to mean 95% full if you're not acting as root).

Either use chown to give yourself ownership (sudo it) or chmod u+rwx the directory you're writing into.

---

### Post by phantomjoker on 2009-12-03
all good people... sorry for the long delay

got it fixed. so basically i had a corrupt file or two on my mobile so just did 

sudo fsck -p /dev/sdb

solved, cheers for the suggestions

---

### Post by M!K3_$ on 2009-12-03
haha, always the little things. no worries. have fun.

---

### Post by hackerlife on 2009-12-04
> please expand? last time i used chmod i completely re-wrote every permission on my system and totally destroyed it. I think i need some instructon


Listen guys I'm seriously sorry for hijacking this thread, but I just really need to know what you did to fix this.
I did something along these lines. I think I fixed most of it but I am still getting occasional errors. (kind of like what you are having now)
thanks, and sorry again.

---

### Post by M!K3_$ on 2009-12-04
you had problems mounting drives? or with chmod/chown/chgrp?

---

### Post by hackerlife on 2009-12-07
Um like one of my drives that I have mounted (and am managing with Storage Device Manager) doesn't let me write, and I don't want to try to change those permissions and risk anything.

Recently I formatted a partition, but don't have correct permissions for that either. (Which strikes me as strange for a fresh format)

I am also having resolution/metamode issues that I think are related

thanks for any and all help

---

### Post by M!K3_$ on 2009-12-08
changing permisions shouldn't risk anything. 

it says that you are using 8.04, maybe all your drive/resolution/metamode issues could be fixed with a 
```
sudo apt-get dist-upgrade
```

---

### Post by hackerlife on 2009-12-08
What would a sudo apt-get dist upgrade do?
I don't wanna upgrade to 9.10, and I guarantee you I am using 9.04. 
(maybe I just haven't updated my profile)
so something like 
sudo chmod 777 /media/sdb1

---

### Post by hackerlife on 2009-12-08
Thanks for the help again

---

