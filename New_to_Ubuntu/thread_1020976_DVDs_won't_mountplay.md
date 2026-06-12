---
title: "DVDs won't mount/play"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by KeepItFunky on 2008-12-24
I just finished installing Ubuntu 8.10 on my Dell Latitude D600, but when I put in a DVD (video, or data) it won't mount on the desktop & I can't access it via VLC/Mplayer.

When I searched, I found something that suggested I should install libdvdread3 & libdvdnav4. I did, but it didn't affect this issue.

Any ideas?

---

### Post by SuperSonic4 on 2008-12-24
```
sudo mount /dev/sr0 /media/cdrom
```

where sr0 is the dvd location. If /media/cdrom doesnt exist enter```
sudo mkdir /media/cdrom
``` in first

---

### Post by Toshibawarrior on 2008-12-24
Then for playback type this on a terminal:

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```

These lackages are also necessary...:) Hope this helps!

---

### Post by Kareeser on 2008-12-24
In my experience, apt won't let you install libdvdcss2 standalone.

I had to download a .deb from [here]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Toshibawarrior on 2008-12-24
Just go to Synaptic, activate Multiverse and Universe sources from Software Sources and press "Reload"...then search for libdvdcss2 and install it. I've never had any problems with Synaptic...and I've never had to use a .deb for it. But it might work too. :)

---

### Post by SuperSonic4 on 2008-12-24
```

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
``` is always good

---

### Post by KeepItFunky on 2008-12-24
> **SuperSonic4 said:**
> ```
sudo mount /dev/sr0 /media/cdrom
```

where sr0 is the dvd location.

This worked the first time I tried it, but then I restarted and the disc wouldn't mount. When I tried it again, it said "No medium found".

---

### Post by KeepItFunky on 2009-01-01
I am still having an issue with this. I have all the standard packages installed; libdvdcss2, libdvdread3, libdvdnav4, vlc even ogle, but the system is not mounting the DVDs when they are inserted.

Any ideas?

---

### Post by mc4man on 2009-01-01
Why don't you stick a dvd in the drive, wait a moment for the drive to settle and then run this to see if the filesystem is being found, ect.

```
sudo lshw -C disk
```

---

### Post by KeepItFunky on 2009-01-01
After putting a disc in it, and running your suggested command, it prints out this about the optical drive:

 *-cdrom
       description: DVD reader
       product: RW/DVD GCC-4243N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: A102
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

Any more ideas?

---

### Post by presence1960 on 2009-01-01
[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

a couple things on this link deal with your situation. check it out. worked for me after installing 8.10 on a friend's machine.

---

### Post by KeepItFunky on 2009-01-01
> **presence1960 said:**
> 
a couple things on this link deal with your situation.

I have actually already installed the packages suggested at your link. I am suspect that there is something deeper rooted here, because even if I didn't have libdvdcss/read/nav installed, the bare system should recognize a disc inserted and mount it, right?

My system is not mounting the disc at all.

---

### Post by mc4man on 2009-01-01
This is indicating that media has been found but no filesystem was detected.

> configuration: ansiversion=5 status=ready
*-medium
physical id: 0
logical name: /dev/cdrom

It's what you'd see if an audio cd or blank disk was in the drive.

> because even if I didn't have libdvdcss/read/nav installed, the bare system should recognize a disc inserted and mount it, right?


Correct (libs, codecs ect. have no bearing on fs detection and mounting

Do you have any other disks to try? (data dvd, data cd, dvd video

While it's a long shot post your fstab

```
cat /etc/fstab
```

edit:

If you have a data cd please try also (anything, even your live cd if you have one

---

### Post by SillySod on 2009-01-01
Hello - I am new to Ubuntu and the forum.  I had the same problem trying to mount a DVD.  All I kept getting was a "Permission denied" error when I tried to click on the DVD icon or navigate to the DVD in the file manager.

It seemed to be that there was no entry for the DVD drive in my "fstab" file.

The only entry was for /dev/scd0 which was my CD writer, but my machine also has a DVD ROM drive and an external DVD writer.

To mount a DVD I had to add a similar line to the /dev/scd0 in my "fstab" file.  This is located in File System/etc.

I duplicated the scd0 line, changing it to scd1 and "cdrom1" in the mount point column:

```

/dev/scd1                     /media/cdrom1  udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/scd2                     /media/cdrom2  udf,iso9660  user,noauto,exec,utf8     0  0  

```
and this worked after saving the file.

By the way - I had to change the file permissions of fstab and open it as super user to be able to edit it.

Hope this helps.

---

### Post by KeepItFunky on 2009-01-01
> **mc4man said:**
> Do you have any other disks to try? (data dvd, data cd, dvd video

While it's a long shot post your fstab

...

edit:

If you have a data cd please try also (anything, even your live cd if you have one
My fstab entry:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9c93ec4e-32f7-44ad-b7ac-c68b6c11b894 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=459cdbf6-cab0-4b2d-ab72-54cab9097d85 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

CDs read and mount fine, it's just DVDs (data, movie, -R, +R,) that aren't recognized.

SillySod, I don't understand enough of what I'm looking at to reconcile it with your suggestion, but I gather that the 'errors=remount' is closer to the crux of the issue.

What would cause that?

---

### Post by SillySod on 2009-01-02
The "errors-remount" looks like it is in an entry for one of your hard disc partitions, so I don't think that's the answer.

If you only have one CD drive then my suggestion won't help as it looks like you already have an entry in your fstab file for the drive.

I noticed that there didn't appear to be an entry in my fstab file for the drive I was using after reading elsewhere about editing the fstab file.  This suggested removing the "udf" part of the entry.  I tried this but it didn't make any difference although it might work for you.

However I would recommend making a note of the changes or saving a backup of the fstab file before doing anything.

---

### Post by KeepItFunky on 2009-01-02
> **SillySod said:**
> The "errors-remount" looks like it is in an entry for one of your hard disc partitions, so I don't think that's the answer.

So, any other ideas then?

mc4man, any red-flags you see here?

What does the fact that the issue seems limited to the recognition of the DVD format suggest? Perhaps there  needs to be a separate entry for DVD even though it's a "combo" drive?

---

### Post by mc4man on 2009-01-02
Well there is always a strong possibility that the drive is at fault, either some dust or dirt or just plain failing.
I'm assuming that your laptop is several years old (3-4+...?)

I know that all dvd **writers** use separate lasers for cd's vs. dvd's so when you can read one or the other only it's usually a drive issue.

I'm not 100 % sure if dvd readers use separate lasers or not.

Whens the last time you could read a dvd?

---

### Post by KeepItFunky on 2009-01-02
> **mc4man said:**
> Well there is always a strong possibility that the drive is at fault, either some dust or dirt or just plain failing.
I'm assuming that your laptop is several years old (3-4+...?)

I know that all dvd **writers** use separate lasers for cd's vs. dvd's so when you can read one or the other only it's usually a drive issue.

I'm not 100 % sure if dvd readers use separate lasers or not.

Whens the last time you could read a dvd?

The last time it was fully operational was when Windows was installed 2 weeks ago... the very first suggestion posted on this thread worked until I rebooted and then not after that, even when I tried the same command.

> **SuperSonic4 said:**
> ```
sudo mount /dev/sr0 /media/cdrom
```

where sr0 is the dvd location. If /media/cdrom doesnt exist enter```
sudo mkdir /media/cdrom
``` in first

---

### Post by mc4man on 2009-01-02
> the very first suggestion posted on this thread worked until I rebooted and then not after that, even when I tried the same command.

You can always mount a file system anywhere as long as the destination directory exists and there is a file system to mount. (even if it's already mounted elsewhere

One of the diffs between 8.10 and earlier is in 8.10 removable disc media can be unmounted but not ejected. So logically speaking it's probable you can insert discs and they will not be auto mounted as is the normal event.

What you can't do is mount (either auto or manually) a disc (file system) that in essence doesn't exist.

I have a new 8.10 install, I'll fool around and see if it's possible to 'break' UDF recognition.

You could insert a dvd and then run dmesg | tail and see if it shows anything.

You could also try commenting out the line in fstab for the dvd drive (/dev/scd0), it's not 100 % necessary 

I have personally had a couple of older drives that worked in xp, but didn't in ubuntu.
While I'm not exactly sure why, my feeling was xp 'waited' out the disc recognition, while ubuntu 'timed out' so to speak

---

### Post by KeepItFunky on 2009-01-03
> **mc4man said:**
> You can always mount a file system anywhere as long as the destination directory exists and there is a file system to mount. (even if it's already mounted elsewhere

One of the diffs between 8.10 and earlier is in 8.10 removable disc media can be unmounted but not ejected. So logically speaking it's probable you can insert discs and they will not be auto mounted as is the normal event.

What you can't do is mount (either auto or manually) a disc (file system) that in essence doesn't exist.

I have a new 8.10 install, I'll fool around and see if it's possible to 'break' UDF recognition.

You could insert a dvd and then run dmesg | tail and see if it shows anything.

You could also try commenting out the line in fstab for the dvd drive (/dev/scd0), it's not 100 % necessary 

I have personally had a couple of older drives that worked in xp, but didn't in ubuntu.
While I'm not exactly sure why, my feeling was xp 'waited' out the disc recognition, while ubuntu 'timed out' so to speak


So are you saying that you think the reason forcing it to mount worked once is because it just happened to recognize there was a disc in there that time, but hasn't since? Wouldn't it have automounted in that case?

I'd assume that if it was hardware age/compatibility, but worked once, I would have been able to duplicate those initial results, even if only intermittently.

I commented out the /dev/scd0

here are the results of the dmesg```
~$ dmesg | tail
[  332.438366] NET: Registered protocol family 10
[  332.440710] lo: Disabled Privacy Extensions
[  332.441744] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  342.476233] wlan0: no IPv6 routers present
[  395.448713] ppdev0: registered pardevice
[  395.496175] ppdev0: unregistered pardevice
[  397.144209] ppdev0: registered pardevice
[  397.192066] ppdev0: unregistered pardevice
[  397.214962] ppdev0: registered pardevice
[  397.264645] ppdev0: unregistered pardevice

```

other oddities I've noticed:
1. There's a '3.1 GB Media' volume that shows up in Nautilus right next to the 'CD-RW/DVD-ROM Drive' and 'Filesystem', and it mounts on the desktop when I click on it.
2. I tried to burn a backup of my home dir with both 'CD/DVD Creator' and 'Brasero', but after confirming the Burn settings all dialogues disappear and there appears to be no progress.

Could either of these issues be related? Maybe the same issue is causing neither the DVD or CD-R to function as expected?

I really appreciate all the help, I'm learning a lot in this whole process.

---

### Post by KeepItFunky on 2009-01-06
Any other thoughts on this subject? It still is not resolved, and I am feeling at a loss here.

---

### Post by CodeNosher on 2009-01-12
I've had the same problem.  Mine started in 7.10.  I wiped it out and installed 8.10.  The DVD worked fine.  I ran it that way for a few days then thought I'd run the updates.  After that it quit.

If I can come up with the time I may wipe it out, put 8.10 on it and run updates one at a time to see which breaks it.  But, I don't have much of an internet connection anymore so I'm not sure when I can get this done.  

Hopefully someone else will solve it and post it here :D

---

### Post by fatsheldon on 2009-01-15
I'm experiencing this exact issue.  Mine seems even more distinct.  I have 3 different dvds I have tried.

1. self-burnt movie with no menus.  mounts/plays just fine.

2. commercial movie Shrek 3.  mounts/plays (gxine for the menus).

3. commercial movie Indiana Jones - Raiders of the Lost Ark.  refuses to mount 99% of the time.  It did mount and I was able to play it in gxine 1 time, but not again since.

When I use the Indiana Jones disc, the drive makes different sounds which made me think it was a hardware failure, but why would these other discs play just fine?

I will look for more information using the suggestions in this thread.

sheldon

---

### Post by KeepItFunky on 2009-01-21
Any headway on these issues? Does *anyone* have any more thoughts?

---

### Post by fatsheldon on 2009-01-22
for my part, I've narrowed my problems to a less than perfect DVD and extra sensitive dvd drive.

A perfectly unscratched DVD will play in Ubuntu and all I've noticed otherwise is occasinally the videa and audio coming unsynched.

---

### Post by KeepItFunky on 2009-01-22
My issue appears to be resolved. Although I don't know what caused the issue.

I am suspect of installation mistakes as it was my first and there was the "extra volume" I mentioned before. I'd mistakenly partitioned the disk a couple times. So I decided to backup my system, and then do a fresh install. Ever since it has worked flawlessly.

I'm glad it's resolved, but sad I can't offer any help to others experiencing the same issue.

> **KeepItFunky said:**
> other oddities I've noticed:
1. There's a '3.1 GB Media' volume that shows up in Nautilus right next to the 'CD-RW/DVD-ROM Drive' and 'Filesystem', and it mounts on the desktop when I click on it.
2. I tried to burn a backup of my home dir with both 'CD/DVD Creator' and 'Brasero', but after confirming the Burn settings all dialogues disappear and there appears to be no progress.

Could either of these issues be related? Maybe the same issue is causing neither the DVD or CD-R to function as expected?

---

### Post by shnurui on 2009-10-26
Fail

those packages are OOD, anyone know where ot get the new ones?

---

