---
title: "Unable to mount cdrom0"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Tholley on 2009-11-16
I have built an old machine and installed 9.10 on it using live CD, so the cdrom was working when I did the install, but now, while I'm checking to make sure music cd's will play, I get nothing.

I go to places and select cdrom0 (which is the only cdrom showing) and I get this error message. Along with what I put in the title, it also says

"mount: special device /dev/scd0 does not exist"

I have put 3 different cd players in and all the same.

---

### Post by sisco311 on 2009-11-16
Open a terminal (Applications -> Accessories -> Terminal) 

and post the output of:
```
sudo lshw -C disk
```
and
```
cat /etc/fstab
```

---

### Post by lrcaballero on 2009-11-16
Hi there!! Welcome to Linux world.....
Insert a cd of your preference and restart your computer, it should show one's computer starts... this is the only thing I can think of right-now. Also check for threads related to cd mount, cd drive, cd drive would not recognize cd's........at search tab!!! Good Luck.... :D

Luis

---

### Post by Tholley on 2009-11-16
maria@maria-desktop:~$ sudo lshw -C disk
[sudo] password for maria: 
  *-disk                  
       description: ATA Disk
       product: WDC WD400BB-00GF
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 09.0
       serial: WD-WMAKA1308685
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=06404b08
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       size: 984MiB (1031MB)
       capabilities: partitioned partitioned:dos
       configuration: signature=00163a1f
maria@maria-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b7c08c9c-1ef4-4dbc-a5e9-e04e46faf9ab /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b37e469c-d199-4d18-a9c3-66f3d297c720 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
maria@maria-desktop:~$

---

### Post by Tholley on 2009-11-17
bump...

---

### Post by ukripper on 2009-11-17
> **Tholley said:**
> bump...

can you post output of the following command:
```
dmesg | grep ATA
```

---

### Post by Tholley on 2009-11-17
> **ukripper said:**
> can you post output of the following command:
```
dmesg | grep ATA
```
 
I should have waited until I got home from work to bump... 
 
I will post the output as soon as I can, when I get back home. 
 
Thanks!

---

### Post by Tholley on 2009-11-17
ok... here is this output...

> maria@maria-desktop:~$ dmesg | grep ATA
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    2.102420] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.102431] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.269544] ata1.00: ATA-5: WDC WD400BB-00GFA0, 09.01B09, max UDMA/100
[    2.285665] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-00GF 09.0 PQ: 0 ANSI: 5
maria@maria-desktop:~$ 

---

### Post by Tholley on 2009-11-18
bump again...
 
how come everytime someone asks me to post an output from terminal, I never get back a reply...;)
 
does it look that bad...

---

### Post by ukripper on 2009-11-19
> **Tholley said:**
> bump again...
 
how come everytime someone asks me to post an output from terminal, I never get back a reply...;)
 
does it look that bad...

naa man I live in uk and time here is GMT when you post I'd be either sleeping or it is off my working hours.

back to your problem.

Now can you reboot and go into BIOS and see if you can see your CD there.

---

### Post by Tholley on 2009-11-19
Going into BIOS was the first thing I tried, but it is password protected and being it is a real old computer and I'm not the orig owner, I don't have the password.
 
The funny thing is, I tried changing cables, thinking maybe I had a bad cable, and with different cables and reboot, it would not even "see" the drive in Places, I put the old cable back in place, it sees it, but just can't mount. 
 
Kind of odd, since I was able to boot from the CD to install 9.10.

---

### Post by Malac on 2009-11-19
> **Tholley said:**
> Going into BIOS was the first thing I tried, but it is password protected and being it is a real old computer and I'm not the orig owner, I don't have the password.
Slightly off topic but try downloading the manual for your motherboard there is usually a jumper settings that resets/un-sets the BIOS password.

---

### Post by Tholley on 2009-11-19
> Slightly off topic but try downloading the manual for your motherboard there is usually a jumper settings that resets/un-sets the BIOS password.
 
Good suggestion, I'll give it a try, but now it is my turn to be at work, and won't be able to see what kind of motherboard it is until about 8 hours or so from now.

---

### Post by ukripper on 2009-11-19
> **Tholley said:**
> Going into BIOS was the first thing I tried, but it is password protected and being it is a real old computer and I'm not the orig owner, I don't have the password.
 
 
Kind of odd, since I was able to boot from the CD to install 9.10.

ok can you post output of these two commands:
```
sudo fdisk -l
```

```
blkid
```

---

### Post by ukripper on 2009-11-19
easiest way to reset BIOS password is to shutodown and poweroff completely unplug power cable . Let the discharge pass-by from your motherboard give it about 30 mins. Then open your case and find a silver button-like-battery (a.k.a CMOS battery) and take it out for about a minute and put it back. Then power on your computer your BIOs password will be gone and BIOs settings will come back to factory default. I have done this several times.

---

### Post by sarwiz on 2009-11-19
I have also done that, but some mobos have a jumper for the password lock. You will need the info on the mobo, but the battery trick also works in most cases.

---

### Post by Tholley on 2009-11-19
> **ukripper said:**
> easiest way to reset BIOS password is to shutodown and poweroff completely unplug power cable . Let the discharge pass-by from your motherboard give it about 30 mins. Then open your case and find a silver button-like-battery (a.k.a CMOS battery) and take it out for about a minute and put it back. Then power on your computer your BIOs password will be gone and BIOs settings will come back to factory default. I have done this several times.
 
 
I'll give it a try when I get home... Thanks for the info!
 
And I'll let you know the outputs from above as well.
 
(only 6 hours to go... ha ha)

---

### Post by sisco311 on 2009-11-19
in the BIOS try to change the AHCI mode to IDE.

[http://ubuntuforums.org/showthread.php?t=1314364]("http://ubuntuforums.org/showthread.php?t=1314364")

---

### Post by Tholley on 2009-11-19
> **sisco311 said:**
> in the BIOS try to change the AHCI mode to IDE.

[http://ubuntuforums.org/showthread.php?t=1314364](http://ubuntuforums.org/showthread.php?t=1314364)

Once I figure out how to reset the bios password... the cmos battery trick did not work, so
I am researching for a mb manual now.

ukripper... if you still need this?

```
maria@maria-desktop:~$ sudo fdisk -l
[sudo] password for maria: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06404b08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
maria@maria-desktop:~$ blkid
maria@maria-desktop:~$ 
```

Also I went into boot menu, and the cdrom is not an option anymore, just gone...

> **sisco311 said:**
> in the BIOS try to change the AHCI mode to IDE.

[http://ubuntuforums.org/showthread.php?t=1314364](http://ubuntuforums.org/showthread.php?t=1314364)

I managed to reset bios password and am in bios now, but do not see anything
showing AHCI. 

1st boot device is IDE-0
2nd was floppy but I changed to CDROM
3rd was CDROM, now floppy

> **ukripper said:**
> naa man I live in uk and time here is GMT when you post I'd be either sleeping or it is off my working hours.

back to your problem.

Now can you reboot and go into BIOS and see if you can see your CD there.

I see CDROM as a boot device...

I changed bios to optimal setting just to see what happens, and then selected boot menu, and still, no CDROM showing.

I'm starting to think it is a motherboard issue...  maybe starting to go bad if not already.

---

### Post by ukripper on 2009-11-20
> **Tholley said:**
> I changed bios to optimal setting just to see what happens, and then selected boot menu, and still, no CDROM showing.

I'm starting to think it is a motherboard issue...  maybe starting to go bad if not already.

Issue seems to be one of below, lets narrow things down with below possibilities:
```
IDE cable is loose at connectors
IDE cable is gone bad and needs replacing
CDROM drive has reached its end.
```

Easy way to test them all is if you have another computer or you can borrow CDROM drive from someone and plug that in and see if that works or not?

---

### Post by Tholley on 2009-11-20
> **ukripper said:**
> Issue seems to be one of below, lets narrow things down with below possibilities:
```
IDE cable is loose at connectors
IDE cable is gone bad and needs replacing
CDROM drive has reached its end.
```Easy way to test them all is if you have another computer or you can borrow CDROM drive from someone and plug that in and see if that works or not?

Already tried 3 different drives, tried 3 different IDE cables, which the other 2 caused the drive to disappear completely. With the original cable, at least I can "see" the CDROM0.

I just tried another drive out of another computer that I know for sure works, and the same thing.

Don't know of this is relevant, but going to Computer, clicking on CDROM0 Properties, there is no applications to Open With. Do I need to add an applications so it will know what to open with?

---

### Post by ukripper on 2009-11-20
ok if you can see your cdrom lets try to forcebly mount it via terminal:
```
sudo mkdir /media/cdrom-test
```
```
sudo mount /dev/scd0 /media/cdrom-test
```

put some cd in drive and then run below:
```
ls -al /media/cdrom-test
```

---

### Post by Tholley on 2009-11-20
Here's what I got...

```
maria@maria-desktop:~$ sudo mkdir /media/cdrom-test
[sudo] password for maria: 
maria@maria-desktop:~$ sudo mount /dev/scd0 /media/cdrom-test
mount: special device /dev/scd0 does not exist
maria@maria-desktop:~$ ls -al /media/cdrom-test
total 8
drwxr-xr-x 2 root root 4096 2009-11-20 09:13 .
drwxr-xr-x 5 root root 4096 2009-11-20 09:13 ..
maria@maria-desktop:~$ 
```

I have reset to boot from cd in bios, and am gonna try to see if it will boot from live cd, and if so, I think I'll just re-install 9.04, since everything worked then.

Well I think that computer is going back in the closet. 
Even after changing the 1st boot device to cdrom, and putting a bootable Live CD in, it still won't do anything. Going to boot menu, cdrom is not even on the list, only ide 0 and floppy. 
Which tells me if I can't cd boot from bios,it is a hardware problem, not a Ubuntu problem.

So I am pretty convinced it is a mb issue, and am gonna just put it away for know.

Thanks for all the suggestions!

---

### Post by ukripper on 2009-11-21
there is no need to decommission your computer. If you want you can use external cdrom or you can get really cheap adapter converter IDE to usb(something like this - [http://www.ebuyer.com/product/130517](http://www.ebuyer.com/product/130517)) and stick your cdrom  and select in bios boot from removable device. 

Otherwise you can just swap the motherboard.

---

### Post by Tholley on 2009-11-21
> **ukripper said:**
> there is no need to decommission your computer. If you want you can use external cdrom or you can get really cheap adapter converter IDE to usb(something like this - [http://www.ebuyer.com/product/130517](http://www.ebuyer.com/product/130517)) and stick your cdrom  and select in bios boot from removable device. 

Otherwise you can just swap the motherboard.

Thanks for he suggestion. It is only a old spare anyway headed for the trash before I decided to intercept it and put it together for a co-worker that has no computer at all.

I don't mind putting my time in, since more of a hobby for me, but do not intend to put any money into it. I'll run across another one headed for the dumpster again sooner or later, then I can peice the two together, and maybe have a decent working system to give to Maria and her family.

Thanks again! :cool:

---

### Post by ukripper on 2009-11-21
Brilliant idea.

 I never thrown a single piece of chip myself. Given it to charity or someone who could actually use it.

Goodluck!:p

---

### Post by Copernicus1234 on 2009-12-02
I managed to get the cdrom working by doing this:

```
sudo mount -t iso9660 /dev/scd0 /media/cdrom 
```

---

### Post by pelgrim on 2009-12-03
I kind of have the same problem here:

I can boot from cd/dvd drive,
but once installed Ubuntu KK it can't mount to de cd/dvd player.

terminal outputs:

pelgrim@pelgrim:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom
mount: special device /dev/scd0 does not exist

---

### Post by ukripper on 2009-12-03
> **pelgrim said:**
> I kind of have the same problem here:

I can boot from cd/dvd drive,
but once installed Ubuntu KK it can't mount to de cd/dvd player.

terminal outputs:

pelgrim@pelgrim:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom
mount: special device /dev/scd0 does not exist

post output of commands:
```
ls -al /dev/cd*
```

```
gedit /etc/fstab
```

```
df -h
```

---

### Post by pelgrim on 2009-12-03
> **ukripper said:**
> post output of commands:
```
ls -al /dev/cd*
```

```
gedit /etc/fstab
```

```
df -h
```

Ok, will do that,
but I'm back at location of that pc on monday.
Till then I hope

> **ukripper said:**
> post output of commands:
```
ls -al /dev/cd*
```

```
gedit /etc/fstab
```

```
df -h
```

The output:
ls -al /dev/cd*
ls: cannot access /dev/cd*: No such file or directory

(that doesn't look promising ...)

/etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c460cd51-5071-43c9-bd22-67c9590b151a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=39666293-8577-4a49-8aa3-57606d939b05 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              18G  2.6G   15G  15% /
udev                  123M  376K  122M   1% /dev
none                  123M  1.1M  122M   1% /dev/shm
none                  123M   76K  123M   1% /var/run
none                  123M     0  123M   0% /var/lock
none                  123M     0  123M   0% /lib/init/rw

help :) (see previous post)

---

### Post by renardmichael on 2009-12-20
I have the exact same problem, I'm from Belgium btw

root@michael:~# ls -al /dev/cd*
ls: kan geen toegang krijgen tot /dev/cd*: Bestand of map bestaat niet
root@michael:~# gedit /etc/fstab
root@michael:~# df -h
Bestandssysteem            Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sda1              71G  3,4G   64G   5% /
udev                  880M  248K  880M   1% /dev
none                  880M  240K  880M   1% /dev/shm
none                  880M  196K  880M   1% /var/run
none                  880M     0  880M   0% /var/lock
none                  880M     0  880M   0% /lib/init/rw
none                   71G  3,4G   64G   5% /var/lib/ureadahead/debugfs

---

### Post by ukripper on 2009-12-21
> **pelgrim said:**
> help :) (see previous post)

Post output of this:
```
ls -al /dev/cd*
```

---

### Post by pelgrim on 2009-12-21
still no solution
and we live in the same conutry, haha

is it a belgian problem ?

---

### Post by BaroqueBloke on 2009-12-24
I have the exact same problem.  Though I'm not dismissing the possibility of the drive having gone faulty, I doubt thats the case.  I burned the install CD that I used to boot Ubuntu on this computer.  As soon as I finish installing, the drive stops working.  

Sadly I did not do a partition and simply clean installed Ubuntu or else id switch over to check.  

I love Ubuntu so far but this is turning into a deal breaker for me.  :cry:

---

### Post by soryu on 2009-12-24
> **Tholley said:**
> I have built an old machine and installed 9.10 on it using live CD, so the cdrom was working when I did the install, but now, while I'm checking to make sure music cd's will play, I get nothing.

I go to places and select cdrom0 (which is the only cdrom showing) and I get this error message. Along with what I put in the title, it also says

"mount: special device /dev/scd0 does not exist"

I have put 3 different cd players in and all the same.



kinda the same problem, when i insert any cd into the drive  the cdrom icon disppears from the- computer- file browser (computer in places) and im unable to play the cd if try to burn the cd i get the "mount:special device does not exist or unable to mountCDrom"
but, i can play the cd using vlc to open it. to burn the cd i used serpentine cd burner . (3)other  cd burning programs  igot the msg unable to mount cdrom

---

### Post by Raymond Petit on 2010-01-06
Good news, guys, the code to force the cdrom to mount is:                sudo mount /dev/hdc /media/cdrom -t udf

First make certain of what your system has designated your cdrom as, mine in the example above is /dev/hdc.  To find yours in the terminal type:
cat /etc/fstab, then press the enter key.  You should find it in the last line.

When you are certain of what your cdrom is called place a dvd in the drive, then type sudo mount /dev/"your cdrom name" /media/cdrom -t udf, then the enter key.

The cdrom should appear on the desktop.  From there you can left click it to select either to play the dvd with movieplayer or vlc.  Mine played flawlessly on an old ibook g4, 1GHz processor with Ubuntu 9.10.

To eject the dvd I have to use the terminal also, right clicking to select "eject" doesn't work.  So after watching movie, in a terminal type:
sudo eject /cdrom/

Interestingly enough, after I did this the first time vlc was somehow able to detect and open a dvd without me having to use the code to force the cdrom to mount, but movieplayer still can't see it so you'll have to use the code first if you want to watch a disk with movieplayer.

Kudos go to DrDevice who gave it to aramumayo in response to 'Unable to mount location, no Media in drive
           9.04-Ubuntu Forums July 2009

---

### Post by Raymond Petit on 2010-01-06
I've been checking, guys, and as far as I know this bug in 9.10 still has not been tracked down and fixed.  Hopefully someone who writes code will solve it soon and the fix will come as an update.  Then all our optical drives will mount automatically as they should.  Use the above work-around and be patient.

---

### Post by slick_nick on 2010-01-14
Same problem here. The drive was working just fine until a reboot today, now I'm getting the "special device does not exist". 

Tried a couple things that haven't worked, will try more this evening, but I wanted to chime in as another user having this issue!

---

### Post by talha06 on 2010-03-27
same problem for me too in ubuntu 9.10... :S

---

### Post by HonzaPokorny on 2010-03-27
> **Copernicus1234 said:**
> I managed to get the cdrom working by doing this:

```
sudo mount -t iso9660 /dev/scd0 /media/cdrom 
```

This doesn't work for me. It still says '/dev/scd0 does not exist'.
Thanks

---

### Post by talha06 on 2010-03-28
[B]please can someone help us??? we're really in a boring situation.. 

Thanx in advance..
With regards,
Talha[/B]

---

