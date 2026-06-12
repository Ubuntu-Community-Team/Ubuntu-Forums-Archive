---
title: "Restored system and now have couple errors ?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Sullr on 2009-01-19
hi,

I wanted some more knowledge on backing up and restoring in Ubuntu so I tested out a really easy command line method posted here at the forums.

I backup up my desktop hard drive with a command like this one...


```
tar cvpzf /media/DATA/BACKUP/UBUNTU/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /
```

I then unplugged hooked up a new hard drive which I did a fresh install of Ubuntu 8.10, at the same time I backed up my fstab and Grub.

I then restored while my new fresh install of Ubuntu was running with this command

first super user

```
tar xvpfz /media/DATA/UBUNTU/backup.tgz -C /
```

Then did what I needed to for grub and fstab.

When I restart I get the following errors

```
Id_static: cannot open output file /lib/modules/2.6.27-9-generic/volatile/ath_rate_sample.ko: Read-only file system
```

I get a bunch of these errors and just the part below changes.

```
ath_rate_sample.ko
```

My system still boots fine and everything is restored as it should be. The permissions of those files are also the same. See attached pic


[URL="http://img261.imageshack.us/my.php?image=dsc00238resizedtd1.jpg"]
[IMG]http://img261.imageshack.us/img261/4351/dsc00238resizedtd1.th.jpg[/IMG][/URL]

---

