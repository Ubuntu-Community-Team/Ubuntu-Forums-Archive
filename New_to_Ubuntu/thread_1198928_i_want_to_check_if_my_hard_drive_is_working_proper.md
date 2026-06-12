---
title: "i want to check if my hard drive is working properly"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by heyyy on 2009-06-28
so any suggestions?

---

### Post by heyyy on 2009-06-28
also my system had a hard drive check so i want to know if it found a problem or is just routine check?

---

### Post by SunnyRabbiera on 2009-06-28
the fsck that comes up is normal, every 20 or so boots it will check the disk for errors.
If there was an error it would have told you, but if it booted in just fine after the check its all good.

---

### Post by rraj.be on 2009-06-28
you can try 

```
sudo hdparm 
```

---

### Post by 3rdalbum on 2009-06-28
> **heyyy said:**
> so any suggestions?

If you're using it, and everything seems fine, then it is physically fine.

If you've just had an automatic filesystem check happen on bootup, then in terms of data integrity it is fine too.

---

### Post by heyyy on 2009-06-30
> **SunnyRabbiera said:**
> the fsck that comes up is normal, every 20 or so boots it will check the disk for errors.
If there was an error it would have told you, but if it booted in just fine after the check its all good.


well it did 3 three times in a row when it booted saying that is a routine check thas why im concerned

---

### Post by oldos2er on 2009-06-30
> **heyyy said:**
> well it did 3 three times in a row when it booted saying that is a routine check thas why im concerned

 Do you mean it checked the same partition three times?

---

### Post by heyyy on 2009-06-30
> **oldos2er said:**
> Do you mean it checked the same partition three times?

each time that i rebooted it it checked the filesystem saying it was a routine check

---

### Post by K.Y.A on 2009-06-30
This means it found errors. You need to boot the livecd, because you CANNOT fsck an active filesystem properly. It will give you a big fat warning message.

Boot the livecd, and fist thing, open a terminal and type:

```
sudo -i
```

This will drop you into a root shell, I highly recommended you press ctrl+D after you are done here so you accidentally don't type in something that could harm your system. Now, type this:

```
fdisk -l
```

that -l is a Lower case L. it should spit out a bunch of partitions. Look for your hard drive (if you only have one, one will be listed). Find teh one that says *Linux* to the right of the one that says ext3, on the same line. It should be like /dev/sda1. Now, once you figure out what drive and partition you would like to scan, type this:
```

fsck /dev/sda1
```

fsck is the command, and scans the device /dev/sda with the first partition. If you would like to scan the secon partition (most likely swap space) the command would be
```

fsck /dev/sda2
```

and so on. /dev/sdb would be your second drive, and then a number constituing to the correct partition. Your welcome ;)

---

### Post by Polaris96 on 2009-06-30
bonnie++ is a good hdd test program.  also hdparm and fsck, as others have mentioned

---

