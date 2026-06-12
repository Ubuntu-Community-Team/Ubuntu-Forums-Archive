---
title: "Stop Ubuntu checking CD drive at boot"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Big_Belly_Bob on 2011-01-31
Hi All,

New to Ubuntu and Linux in general, have taken the time to learn some basic command line and have fixed a few problems I've been having but there's one thing still kinda bugging me.

Whenever I boot in to Ubuntu it seems to check the CD Drive?? it's not my computer checking the drive (i.e. it's not set that way in the BIOS, it's booting from the HDD) but it still checks it prior to loading the log on screen

I'm sure this must slow the boot time a bit since presumably the computer waits for a response from the CD drive before completing the boot but the main reason I don't like it is that it just seems unnecessary - if I wanted to boot from the CD Drive then I would, I'd change the BIOS to check the CD Drive first, so I don't understand why it does it?

Does anyone know why Ubuntu checks the CD Drive? (presuming it's not just me) and does anyone know who to stop it?

Thanks :)

---

### Post by HereInOz on 2011-01-31
Probably a silly question but is there a CD in the drive at the time?  That is the only reason I can think of.

---

### Post by drs305 on 2011-01-31
You can check to see if you have an fstab entry which is trying to mount the cdrom. If you do, placing a # symbol at the start of the line will prevent it being loaded when fstab is read. You can edit fstab with this command:
```
gksu gedit /etc/fstab
```

---

### Post by Big_Belly_Bob on 2011-02-01
Definitely no CD in the drive but not a silly question since I have been known to do that! ;)

I'm not seeing anything in the fstab file that looks like a CD drive but that might be because I'm still learning Linux

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
```As I understand it /dev/sda1 would be my hard drive? which would explain the ext4 after it, the /proc I'm not sure about but I'm going to guess processor?

Am I reading the fstab file correctly? if so does anyone have any other ideas?

---

### Post by LowSky on 2011-02-01
how slow is your boot time really? 35-60 seconds. If its such an issue use Suspend or Hibernate.

If a disk is present it is only trying to have it available for when you log in. If not, people would complain (on here) that the CD/DVD isn't mounted and how to do that. 

Here is my fstab, its much more complex, but works the same way.

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=511bd2f1-72da-4726-8550-50073f7793e3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=0e040412-6778-405a-af1e-23ddeea08080 /home           ext4    defaults        0       2
# /media/SAMSUNG750GB was on /dev/sdb1 during installation
UUID=bcae2dde-e188-4dc6-984d-d8899944ade2 /media/SAMSUNG750GB ext4    defaults        0       2
# /media/SEAGATE500GB was on /dev/sdd1 during installation
UUID=864d7905-2b53-4b8f-9911-c2395343887a /media/SEAGATE500GB ext4    defaults        0       2
# /media/WD1TB was on /dev/sdc3 during installation
UUID=47697fb0-72b2-46b1-97af-9bb61ac6c23f /media/WD1TB    ext4    defaults        0       2
# /media/WD2TB was on /dev/sda4 during installation
UUID=80465a59-cede-410d-9543-b7b438737278 /media/WD2TB    ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=b69bd3d9-f9cb-4285-aa90-1d5b28dfaa4b none            swap    sw              0       0


```

see this to explain /proc
[http://www.linux.com/archive/feature/126718](http://www.linux.com/archive/feature/126718)

---

### Post by davidmohammed on 2011-02-01
*deleted*

---

### Post by Big_Belly_Bob on 2011-02-01
> **LowSky said:**
> how slow is your boot time really? 35-60 seconds. 

Probably not even that, but you learn nothing from ignoring a problem or using a work around like hibernate - today for example I've learnt that there's something called fstab :) and thanks for the /proc link by the way :)

The reason I originally spotted it was because it used to give an error message after checking (I presumed it was related since it always popped up immediately after) however I had bigger problems at the time and the error message disappeared after a kernel update before I noted it down, now I just get a blank screen for a bit while it checks the drive.

The thing is Windows doesn't check so I don't know why Ubuntu needs to, if it's a normal part of Ubuntu that's fine but if it's not it's going to bug me not understanding why it's happening.

Either way I'll leave the Thread open for a bit to see if anyone has any ideas, if not I'll mark it solved and ignore it.

---

### Post by Big_Belly_Bob on 2011-02-02
Thanks to anyone who contributed :)

---

### Post by meamusta on 2012-05-11
This thing is bugging me as well. Now I have a new silent laptop with ssd drive and it doesn't give any sounds during the boot except 3-4 "crank"s. I quess it is from the cd drive. I would understand if it happens once, but why Ubuntu needs to check the drive 3-4 times during the boot? The boot takes only a few seconds, so for me this is purely a noice issue.

edit: I'm using 12.04

---

