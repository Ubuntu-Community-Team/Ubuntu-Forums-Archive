---
title: "why will HD not unmount...Busy doing what exactly"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by sonny123 on 2009-10-21
cant unmount external USB HD, cant read it or write to it
Am new to linux, followed some advice on various forums etc  but not really sure what i'm doing, help greatly appreciated
here are some blurbs from terminal :confused:

sonny@rock:~$ sudo mount
 
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
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sonny/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sonny)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


sonny@rock:~$ sudo umount /dev/sdb1
 
umount: /media/disk: device is busy.
        (In some cases useful info about processes that use the device is found by lsof(8) or fuser(1))

sonny@rock:~$ fuser -m /dev/sdb1
/dev/sdb1:            3301

sonny@rock:~$ ps auxw|grep 3301
sonny     3301  0.0  1.3  67332  2896 ?        Dl   01:43   0:04 nautilus
sonny    20118  0.0  0.3   3344   812 pts/1    S+   10:47   0:00 grep 3301

sonny@rock:~$ sudo lsof /dev/sdb1
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/sonny/.gvfs
      Output information may be incomplete.
COMMAND   PID  USER   FD   TYPE DEVICE  SIZE NODE NAME
nautilus 3301 sonny   32r   DIR   8,17 16384    1 /media/disk

Thanks in advance

---

### Post by patrickaupperle on 2009-10-21
> **sonny123 said:**
> 
<snip>
sonny@rock:~$ sudo lsof /dev/sdb1
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/sonny/.gvfs
      Output information may be incomplete.
COMMAND   PID  USER   FD   TYPE DEVICE  SIZE NODE NAME
**nautilus** 3301 sonny   32r   DIR   8,17 16384    1 /media/disk

Thanks in advance

I can not gaurantee that this is the issue, but, looking at that output, I would assume nautilus is using the device. Do you have any nautilus windows open? If not, you could try: ```
killall nautilus
``` Then it should unmount.

---

### Post by sonny123 on 2009-10-21
Thanks patrick have just tried that here is what happened

sonny@rock:~$ killall nautilus
sonny@rock:~$ sudo umount /dev/sdb1
umount: /media/disk: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
sonny@rock:~$ 


Which is no change..  but thanks

---

### Post by Dougie187 on 2009-10-21
I think what you really want is something like this.
```
cd ~
sudo umount /media/disk
```

As /dev/sdb1 is the device, and the device is mounted to some mountpoint (i am assuming it is /media/disk) you want to unmount the mount point. Also, you can't unmount something when you are inside of that directory, so if you have a terminal open in /media/disk and you are trying to unmount /media/disk you can't unmount that and it will return busy.

Edit:

After re-reading some of the other posts, after you did
```
killall nautilus
```

Did you follow it up with 
```
ps aux | grep "nautilus"
```
?

If you did, and it was still running, did you try ```
pkill nautilus
```?

---

### Post by sonny123 on 2009-10-21
Thank you Dougie 
Here is what ive done since your post...

> sonny@rock:~$ killall nautilus
sonny@rock:~$ sudo umount /dev/sdb1
[sudo] password for sonny: 
umount: /media/disk: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
sonny@rock:~$ ps aux | grep "nautilus"
sonny     3301  0.0  0.9  67332  1960 ?        Dl   01:43   0:04 nautilus
sonny    26784  0.0  0.3   3344   812 pts/1    S+   14:35   0:00 grep nautilus
sonny@rock:~$ pkill nautilus
sonny@rock:~$ ps aux | grep "nautilus"
sonny     3301  0.0  0.9  67332  1964 ?        Dl   01:43   0:04 nautilus
sonny    26788  0.0  0.3   3344   812 pts/1    S+   14:36   0:00 grep nautilus
sonny@rock:~$ sudo umount /dev/sdb1
[sudo] password for sonny: 
umount: /media/disk: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

still no access to drive .. still confused  

i dont think i've got a terminal open in /media/disk but to be honest i dont know or know how to check where terminal is running.
if it helps ubuntu is clean installed (no windows or any thing) on my main HD.  the ext drive is FAT 32 and partition was creatd with Gparted. i then copied files to it from a vista machine. the vista machine wont see the drive either

---

### Post by patrickaupperle on 2009-10-21
Ok, like I said, I am not a professional. This should work, though it is not a desirable way of doing things. 
What you could do it switch to a virtual terminal (Ctrl Alt F1) and logging in. After that stop GDM. I use arch linux currently, so I am not sure the exact command, probably something like "/etc/init.d/gdm stop" without the quotes. Then run the umount command. This should work at this point. You can start gdm again with "/etc/init.d/gdm start" or whatever. Maybe someone else can fix those commands. Try that.

---

### Post by Dougie187 on 2009-10-21
I think those commands should work, but I think the preferred way of doing it is something like
```
sudo service gdm stop
```

However, did you try this
```
sudo umount /media/disk
```?

It looks like you are always trying to unmount /dev/sdb1. I am unsure if it will work, but I have never unmounted anything like that before.

---

### Post by The Cog on 2009-10-21
Usually, it's because either because you have a command prompt open with that disk as its current directory, or because nautilus is holding it open. If it's a command prompt sitting on the disk, changing the working directory will do the trick. But in this case, it looks like nautilus is the offending process. I'm not sure why killing nautilus doesn't do the trick. Sometimes this works when all else fails though:
```
sudo umount -l /media/disk
```

---

### Post by kgas on 2009-10-21
A continuous glow HD LED (red) is a symptom of HD dying.I lost one wise 80 GB hd recently. Is your HD getting detected in other OS?.

---

### Post by sonny123 on 2009-10-21
Thanks very much to every one havent got time to try every thing here till ive put the ankle biters to bed!  

Kgas   drive cannot been seen by windows although i wrote it with windows.. on another forum i read this might have caused the problem , if the device wasnt removed properly from the windows machine

will post back results of other commands

---

### Post by ikisham on 2009-10-21
Just to reinforce: the command you should use is ```
sudo umount /media/disk
```and _not_ ```
sudo umount /dev/sdb1
```

---

### Post by sonny123 on 2009-10-21
Dougie  not sure myself of the difference between 

unmount /dev/sdb1    and 
unmount: /media/disk

but both give the same result
sonny@rock:~$ sudo umount /dev/sdb1
umount: /media/disk: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
sonny@rock:~$ sudo umount /media/disk
umount: /media/disk: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

---

### Post by Dougie187 on 2009-10-21
> **sonny123 said:**
> Dougie  not sure myself of the difference between 

unmount /dev/sdb1    and 
unmount: /media/disk

but both give the same result
sonny@rock:~$ sudo umount /dev/sdb1
umount: /media/disk: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
sonny@rock:~$ sudo umount /media/disk
umount: /media/disk: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

Did you try ```
sudo umount -l /media/disk
``` as was previously mentioned. I only suggested that because I didn't know if unmounting the device from /dev would be the same as unmounting from the mount point in /media, though I have tried it since then and both of them work.

EDIT: Also, just so you know. Depending on the format of the drive windows might not see it, or it might need a specific driver to see it. So just because windows doesn't see it doesn't mean that it is dead/dying or anything of that sort.

Also, I don't see why it would help any, but you can try
```
sudo kill -9 3301
```
just to try to kill nautilus again. This thread is starting to be more about how to kill nautilus than how to unmount your drive.

---

### Post by WaiWaiWario on 2009-10-21
You might give the fuser command a try.

[http://www.idevelopment.info/data/Unix/General_UNIX/GENERAL_Troubleshootingthedeviceisbusy.shtml](http://www.idevelopment.info/data/Unix/General_UNIX/GENERAL_Troubleshootingthedeviceisbusy.shtml)

Quick little guide there to get you familiar with the command.

Pretty much, you'll want to do:
```
 sudo fuser -k /media/disk 
```

That should kill all processes of any kind accessing that folder. You should be able to unmount it then.

---

