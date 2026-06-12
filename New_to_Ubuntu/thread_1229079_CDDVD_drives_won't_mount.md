---
title: "CD/DVD drives won't mount"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by dkolars on 2009-08-01
I have 2 internal hdd's (HD 1 & HD 2), and an external (FreeAgent Drive)
I have an internal CD/DVD player, and internal CD/DVD burner, and an external DVD burner.

Using Ubuntu 9.04.

NONE of the CD/DVD drives will mount.  The CD drive used to play CD's, but now will not...  Just did an update yesterday, so maybe that was it?  I've not used the DVD drives since I switched to Ubuntu about 4 weeks ago... I'm on the road a lot, so haven't spent the full 4 weeks using it, more like 2-3...

I've gone into System, Computer and attempted to mount them and get the following:

CD-RW/DVD-ROM Drive = Unable to mount location... No media in the drive.
CD-RW/DVD RW±Drive = Unable to mount location... Can't mount file.
CD-RW/DVD RW±Drive = Unable to mount location... No media in the drive.

I think that Ubuntu can see them?:

dkolars@Desktop:~$ ls -l /media
total 60
lrwxrwxrwx 1 root root     6 2009-06-30 09:39 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2009-06-30 09:39 cdrom0
drwxr-xr-x 2 root root  4096 2009-06-30 09:39 cdrom1
drwxr-xr-x 2 root root  4096 2009-06-30 09:39 cdrom2
drwxr-xr-x 2 root root  4096 2009-06-30 09:39 cdrom3
drwxrwxrwx 1 root root  4096 2009-07-20 11:22 FreeAgent Drive
drwxrwxrwx 1 root root 28672 2009-07-20 12:03 HD 1
drwxrwxrwx 1 root root 12288 2009-07-20 11:22 HD 2
dkolars@Desktop:~$ mount /media/cdrom0
mount: no medium found on /dev/sr0
dkolars@Desktop:~$ mount /media/cdrom1
mount: can't find /media/cdrom1 in /etc/fstab or /etc/mtab
dkolars@Desktop:~$ mount /media/cdrom2
mount: can't find /media/cdrom2 in /etc/fstab or /etc/mtab
dkolars@Desktop:~$ mount /media/cdrom3
mount: special device /dev/scd3 does not exist

Here's my /media/.hal-mtab file contents:
/dev/sdg1    1000    0    ntfs-3g    nosuid,nodev,uhelper=hal,locale=en_US.UTF-8,exec    /media/FreeAgent Drive
/dev/sda2    1000    0    ntfs-3g    nosuid,nodev,uhelper=hal,locale=en_US.UTF-8,exec    /media/HD 1
/dev/sdb5    1000    0    ntfs-3g    nosuid,nodev,uhelper=hal,locale=en_US.UTF-8,exec    /media/HD 2
-----
Here's my fstab file:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bb687805-94d4-46de-8bd8-8d4c772848d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd3       /media/cdrom3   udf,iso9660 user,noauto,exec,utf8 0       0
-----

Any suggestions?  I've cruised the bulletin boards, but have found stuff that 1) doesn't seem to apply (from 2005, 2006, etc.), or 2) that I have no clue what they are talking about!

Also, on some terminal screens, I get the result that I should use that command as a super-user... what means this?

Thanks in advance!!! DK  [www.davekolars.com]("http://www.davekolars.com")

---

### Post by ecmatter on 2009-08-01
I have a similar problem.  After an extremely frustrating week of trying to find a solution, I gave up.  

Bad kernel + Low priority =  Dead drive

Good Luck.

---

### Post by Bibbleycheese on 2009-10-10
Sounds like the same problem I'm having.
 I've got an external IDE drive box, which can take either a hard drive or an optical drive.
Currently it's got a DVD ROM drive in.
I did manage to get it to work on Hardy, after much fiddling around.
Now I've upgraded to Jaunty, I can't get it to work and I can't remember what I did before.
The machine I'm using hasn't got room in the case for a CD drive, so I did the install with the case open and a CD drive connected to the second IDE connector.
Now it's all closed up again I was hoping that the external DVD would just plug and play. No luck.

I've tried adding other external HDDs and USB sticks, and these all plug and play fine - its just this External Optical Drive.
I've also tried it on a USB cable that is known to be working. Still no good.:confused:
I guess its something in fstab? but I haven't a clue what to do. Can anyone hep?

---

### Post by Bibbleycheese on 2009-10-10
Ahh, now this is interesting.
I've tried the same drive in a different external USB enclosure and it works.
The disk just pops up on the desktop and appears in my Places list - Hooray.
So, the problem, is with the USB drive enclosure I was using - for some reason Jaunty won't recognise it.
I wonder why?
What would I have to do to see if Jaunty was detecting the external drive, but not knowing what to do with it?

---

### Post by praveesh on 2009-10-10
I think this is an issue of version 9.04 . Me and my friends using Ubuntu have the save problem. The next version of Ubuntu 9.10 will be released in this month . Most probably, that will solve the issue .

---

### Post by MrWES on 2009-10-10
Try

```
sudo mount /dev/sr0 /media/cdrom0
```

sudo = super-user-do (aka administrator type rights)

Bill

---

### Post by MrWES on 2009-10-10
> **Bibbleycheese said:**
> Ahh, now this is interesting.
I've tried the same drive in a different external USB enclosure and it works.
The disk just pops up on the desktop and appears in my Places list - Hooray.
So, the problem, is with the USB drive enclosure I was using - for some reason Jaunty won't recognise it.
I wonder why?
What would I have to do to see if Jaunty was detecting the external drive, but not knowing what to do with it?

Plug the drive in, and then open a terminal and check dmesg for errors

```
dmesg | tail
```

---

### Post by arst06d on 2010-05-14
Hi

I have a similar problem in that I have an Acer Aspire Revo tiny desktop installed with Ubuntu 10.04.  I have two external hard drives plugged in and recognised no problem:

 ```
david@acer-revo-01:~$ ls -l /media
total 12
drwx------ 1 david david 8192 2010-05-13 13:07 BUFFALO
drwx------ 1 david david 4096 2010-05-13 19:08 SimpleDrive
david@acer-revo-01:~$ 

```

I will obviously need to use a cd/dvd at some stage and I have an old external case into which I have placed the dvd drive from my old pc, attached to the revo by USB.

When I switch on, it looks like the OS tries to mount it, 'cos I can see it in Computer (see screenshot), but it disappears when I insert a CD, and it never appears under Places.

MrWes suggested running:
```
david@acer-revo-01:~$ dmesg | tail
[ 2379.344814] sr 14:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2379.344828] sr 14:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 2379.344841] sr 14:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 2379.344859] sr 14:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00 00 00
[ 2379.344889] end_request: I/O error, dev sr0, sector 0
[ 2379.348814] sr 14:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2379.348828] sr 14:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 2379.348841] sr 14:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 2379.348859] sr 14:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00 00 00
[ 2379.348888] end_request: I/O error, dev sr0, sector 4096

```
 

Now I have no idea what this means.  I see "illegal request", "illegal mode", "I/O error" etc but what does it all mean, and what do i have to do to get the thing working?

I've tried checking the obvious ie that the drives jumper is set to Master rather than Slave, but after that I'm lost.

I should also add that when I go into System>Administration>Disk Utility I can see the drive listed - it even allows me to eject the tray!  See attached screenshot.  However, when I try to safely remove I get an error message (screenshot attached).



Any help will be greatly appreciated.

---

### Post by alejandro.mc on 2010-05-26
Same issue here..

---

### Post by vayu on 2010-05-27
I have same problem. My system won't mounts CD's or DVD's.  If I boot with a CD or DVD in the drive then my system will read it.  After a while from boot time it won't recognize the drive anymore.
Anyone have any ideas?

---

### Post by raj_bharathi on 2010-06-14
i just burnt a dvd . everything went smoothly and it ejected as expected. i put the dvd back to check the contents when it displays the "unable to mount volume" dialog box saying "invalid mount option as the reason".. am unable to understand this because i had been burning and reading dvds without any problems previously, but i cant understand what is happening now.

i checked the older dvds  and they work just fine.. i  really dont know what to do now!!!!
please help!!

---

### Post by marcoftheknight on 2010-06-14
Sudo mount -a
see what that gives you should show the hard drive and any DVD drives and wethere they Are mounted r not thanks
lol post on iPhone (ukniwuraddicted when)

---

