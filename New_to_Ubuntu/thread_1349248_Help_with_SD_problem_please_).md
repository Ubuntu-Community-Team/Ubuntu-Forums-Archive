---
title: "Help with SD problem please :)"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by FuneralQueen on 2009-12-08
Hi there

Been having some problems with Ubuntu, I tried googling it etc but didn't seem to find the exact solution!

Basically I have a Nokia 5800 Express with a 2Gig SD card. I've been transferring music ok, with no problems, but now for some reason it's showing up as a "Read Only" disk - so I can't transfer to it anymore. 

Everything I googled came up for people using a USB adapter - not a phone, so I'm not sure if that's the problem?

I'd like to be able to transfer stuff again!

Hopefully someone can give me an easy to understand solution :)

Thanks!

---

### Post by FuneralQueen on 2009-12-08
Bump :)

---

### Post by rossmoore on 2009-12-08
Hi.

So I presume you're plugging your phone, with the SD card, in by USB cable? Is this as simple as a permissions problem - if you right click on the drive and select properties, can you change it to "read and write" access?

Alternatively it might be that the file system has become a little corrupted because the SD card or phone was removed without first unmounting. The way to fix this, I think, is to unmount it (right click on the disk on your desktop and select "Unmount") and then run fschk against the relevant /dev/sd*. Does that make sense to you, or do you need more step-by-step instructions?

Etiquette rules are that bumping is only really allowed after 24 hours, by the way.

---

### Post by FuneralQueen on 2009-12-08
> **rossmoore said:**
> Hi.

So I presume you're plugging your phone, with the SD card, in by USB cable? Is this as simple as a permissions problem - if you right click on the drive and select properties, can you change it to "read and write" access?

Alternatively it might be that the file system has become a little corrupted because the SD card or phone was removed without first unmounting. The way to fix this, I think, is to unmount it (right click on the disk on your desktop and select "Unmount") and then run fschk against the relevant /dev/sd*. Does that make sense to you, or do you need more step-by-step instructions?

Etiquette rules are that bumping is only really allowed after 24 hours, by the way.

Ack! Sorry.

Step by step instructions would be wonderful, thank you.

---

### Post by ukripper on 2009-12-08
Go to terminal, post output of following command:
```
df -h
```

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> Go to terminal, post output of following command:
```
df -h
```

```

Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             144G   22G  116G  16% /
udev                  497M  280K  497M   1% /dev
none                  497M  1.2M  496M   1% /dev/shm
none                  497M  304K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sdb1             1.9G  1.2G  749M  62% /media/NOKIASD
```Is that right? :)

---

### Post by ukripper on 2009-12-08
yeh taht is right.
ok now post output of this:
```
ls -al /media//NOKIASD
```

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> yeh taht is right.
ok now post output of this:
```
ls -al /media//NOKIASD
```

```
ls: cannot access -: No such file or directory
ls: cannot access al: No such file or directory
ls: cannot access /media//NOKIASD/Games: Input/output error
/media//NOKIASD:
Games  Images  Installs  Music  Others  Photos  Private  Sounds  sys  Videos 
```Well that looks encouraging :eek:

---

### Post by rossmoore on 2009-12-08
ukripper made a slight typo, that should have read:
ls -al /media/NOKIASD

---

### Post by ukripper on 2009-12-08
i am sorry, rossmoore is right. i made a typo:

Can you post output of this please:
```
ls -al /media/NOKIASD
```

---

### Post by FuneralQueen on 2009-12-08
Mmm the same thing came up ??
(Am I right in assuming that there was two /'s in the first and only one / in the second..?)

---

### Post by ukripper on 2009-12-08
> **FuneralQueen said:**
> Mmm the same thing came up ??
(Am I right in assuming that there was two /'s in the first and only one / in the second..?)

yes. you are right in thinking that. can you try with the second command i gave you. Same thing won't come-up if you put the second command.

---

### Post by FuneralQueen on 2009-12-08
Umm for some reason the same thing DID come up??

The only thing I can think may have caused this - when I posted the first "output", I renamed the SD Card - it was originally (MyName SD) (space included) - I renamed it NOKIASD for the sake of the post - but then manually renamed the SD (in an older Nokia phone) to reflect this change..

Could the original "space" between the name of the SD card caused this..?

(I realize that was a bit of a confusing post :) )

---

### Post by ukripper on 2009-12-08
> **FuneralQueen said:**
> Umm for some reason the same thing DID come up??

The only thing I can think may have caused this - when I posted the first "output", I renamed the SD Card - it was originally (MyName SD) (space included) - I renamed it NOKIASD for the sake of the post - but then manually renamed the SD (in an older Nokia phone) to reflect this change..

Could the original "space" between the name of the SD card caused this..?

(I realize that was a bit of a confusing post :) )

can you post output of this command without renaming anything now:
```
df -h
```

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> can you post output of this command without renaming anything now:
```
df -h
```

Ok, here we go (again, thank you for your patience :) )

```

Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             144G   22G  116G  16% /
udev                  497M  280K  497M   1% /dev
none                  497M  1.2M  496M   1% /dev/shm
none                  497M  284K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sdb1             1.9G  1.2G  749M  62% /media/NOKIASD

```(It is "really" renamed this time :) )



Looking back on it though, it looks the same? Even though I did actually physically change the name of the card..

---

### Post by ukripper on 2009-12-08
ok can you post output of this command then:
```
sudo ls -al /media/NOKIASD
```

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> ok can you post output of this command then:
```
sudo ls -al /media/NOKIASD
```

Here we go..

```

ls: cannot access /media/NOKIASD/Games: Input/output error
total 356
drwx------ 13 debbie debbie 16384 1970-01-01 08:00 .
drwxr-xr-x  4 root   root    4096 2009-12-08 20:35 ..
d?????????  ? ?      ?          ?                ? Games
drwx------  6 debbie debbie 32768 2009-12-06 06:07 Images
drwx------  2 debbie debbie 32768 2009-12-07 22:58 Installs
drwx------ 12 debbie debbie 32768 2009-12-06 19:45 Music
drwx------  3 debbie debbie 32768 2009-12-07 22:58 Others
drwx------  6 debbie debbie 32768 2009-12-06 19:46 Photos
drwx------  7 debbie debbie 32768 2009-12-05 09:16 Private
drwx------  4 debbie debbie 32768 2009-12-07 22:58 Sounds
drwx------  4 debbie debbie 32768 2009-12-07 23:09 sys
drwx------  4 debbie debbie 32768 2009-12-05 17:13 .Trash-1000
drwx------  2 debbie debbie 32768 2009-12-07 06:19 Videos

```

---

### Post by ukripper on 2009-12-08
if you are logged in as a user "debbie" than you shouldn't have any problem writing to that folder. Can you confirm you are logged is as debbie?

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> if you are logged in as a user "debbie" than you shouldn't have any problem writing to that folder. Can you confirm you are logged is as debbie?

Yes, I am.

I just double checked again (to see if I'm going crazy) by dragging and dropping a music file from (my computer) to the phone/SD card - and again I got the error;

"Error while copying to "Music""
The destination is read only"

This is probably something really obvious/easy to understand for a skilled Ubuntu user (clearly I am not one) :)

---

### Post by ukripper on 2009-12-08
> **FuneralQueen said:**
> Yes, I am.

I just double checked again (to see if I'm going crazy) by dragging and dropping a music file from (my computer) to the phone/SD card - and again I got the error;

"Error while copying to "Music""
The destination is read only"

This is probably something really obvious/easy to understand for a skilled Ubuntu user (clearly I am not one) :)

ok run this command in terminal and see if you can transfer files afetr that:
```
sudo chmod 755 -R /media/NOKIASD
```

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> ok run this command in terminal and see if you can transfer files afetr that:
```
sudo chmod 755 -R /media/NOKIASD
```

Ok, I ran the command and a (pretty long) list went through the terminal, basically for EVERY file on the SD card this came up -


```

chmod: changing permissions of `/media/NOKIASD/Music/Grotesque - Museum of Human Disease/10 Omnipotent Antipode.mp3': Read-only file system

```

.. literally, for every file. I tried to transfer again after running that command - and it's still not letting me transfer (?!)

(Thank you again, I hope this isn't driving you crazy!)

---

### Post by ukripper on 2009-12-08
Can you post output of this command:
```
ls -al /media/NOKIASD/Music
```

and this:
```
mount
```

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> Can you post output of this command:
```
ls -al /media/NOKIASD/Music
```and this:
```
mount
```

Ok, for the first bit it is also very long so a snapshot would be - 
```

drwx------  3 debbie debbie    32768 2009-11-15 19:29 She, A Female Trip Hop Experience
drwx------  3 debbie debbie    32768 2009-10-31 15:38 Sneaker Pimps - Becoming X
drwx------  3 debbie debbie    32768 2009-10-31 15:27 Sohodolls - Ribbed Music For The Numb Generation
-rwxr-xr-x  1 debbie debbie  5883712 2008-12-25 22:30 SPL & TZA - Violation.mp3
-rwxr-xr-x  1 debbie debbie 13719552 2009-06-06 11:00 Spor - Valentine [320].mp3

```

I have a lot of music on there so I figure it would be a longer post :)

the second bit;

```

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/debbie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=debbie)
/dev/sdb1 on /media/NOKIASD type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

---

### Post by ukripper on 2009-12-08
ok let us apply different approach.

follow these steps:

This will unmount your current directory
```
sudo umount /media/NOKIASD
```

This will create new directory for mounting
```
sudo mkdir /media/sdcard
```

This will mount your sd card on the directory you created i.e. /media/sdcard
```
sudo mount -t  vfat  -o iocharset=utf8,umask=000 /dev/sdb1 /media/sdcard 
```




once mounted run this command and post output here:
```
ls -al /media/sdcard
```

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> ok let us apply different approach.

follow these steps:

This will unmount your current directory
```
sudo umount /media/NOKIASD
```This will create new directory for mounting
```
sudo mkdir /media/sdcard
```This will mount your sd card on the directory you created i.e. /media/sdcard
```
sudo mount -t  vfat  -o iocharset=utf8,umask=000 /dev/sdb1 /media/sdcard 
```


once mounted run this command and post output here:
```
ls -al /media/sdcard
```

Ok .. here :)

```

ls: cannot access /media/sdcard/Games: Input/output error
total 356
drwxrwxrwx 13 root root 16384 1970-01-01 08:00 .
drwxr-xr-x  4 root root  4096 2009-12-08 21:35 ..
d?????????  ? ?    ?        ?                ? Games
drwxrwxrwx  6 root root 32768 2009-12-06 06:07 Images
drwxrwxrwx  2 root root 32768 2009-12-07 22:58 Installs
drwxrwxrwx 12 root root 32768 2009-12-06 19:45 Music
drwxrwxrwx  3 root root 32768 2009-12-07 22:58 Others
drwxrwxrwx  6 root root 32768 2009-12-06 19:46 Photos
drwxrwxrwx  7 root root 32768 2009-12-05 09:16 Private
drwxrwxrwx  4 root root 32768 2009-12-07 22:58 Sounds
drwxrwxrwx  4 root root 32768 2009-12-07 23:09 sys
drwxrwxrwx  4 root root 32768 2009-12-05 17:13 .Trash-1000
drwxrwxrwx  2 root root 32768 2009-12-07 06:19 Videos

```

---

### Post by ukripper on 2009-12-08
ok can you try to transfer files now to music folder? if that works then we will make this permanent. Actually i have to go somewhere for an hour now. i will be back, someone else surely will pickup from here and will help you out making this solution permanent.

---

### Post by FuneralQueen on 2009-12-08
> **ukripper said:**
> ok can you try to transfer files now to music folder?

Ack! Still not working :(

(Getting the same "read only" error..)

Could it be the SD card itself?

---

### Post by ukripper on 2009-12-08
> **FuneralQueen said:**
> Ack! Still not working :(

(Getting the same "read only" error..)

Could it be the SD card itself?
can you post output of this comamnd again:
```
df -h
```

```
sudo blkid
```

```
dmesg | tail
```

---

