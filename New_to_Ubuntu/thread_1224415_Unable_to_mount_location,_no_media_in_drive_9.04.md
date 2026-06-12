---
title: "Unable to mount location, no media in drive 9.04"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by amarumayo on 2009-07-27
Hi all, Newb here.  I just installed Ubuntu 9.04 on my Acer Aspire 4810Tz-4696 and most things are working great.  I cannot however get the DVD drive to read media.  The disc won't spin and when I click on the drive in Places I get the following message:

Unable to mount location
No media in the drive

Thanks for any help!!

Chris

---

### Post by TeoBigusGeekus on 2009-07-27
Have you tried with different cds/dvds? Music, data, video - any difference?

---

### Post by amarumayo on 2009-07-27
Thanks for the reply
Yes I have.  Only DVD's though I have not tried CDs I don't have any with me.  I know the drive works because I used it to install ubuntu.

Thanks

---

### Post by TeoBigusGeekus on 2009-07-27
Hmm...
Could be a tricky format you've used in windows (I assume your dvds were burned in windows).
Put an empty dvd in the drive and try to burn some data. Then see if ubuntu can read it.

---

### Post by amarumayo on 2009-07-27
I actually burned the ubuntu download in Ubuntu 7.04 on my old computer that is now kaput.  I don't have blank dvd's right now, but I will try it when I get home.

Thanks again

---

### Post by Genesis3 on 2009-07-27
> **TeoBigusGeekus said:**
> Hmm...
Could be a tricky format you've used in windows (I assume your dvds were burned in windows).
Put an empty dvd in the drive and try to burn some data. Then see if ubuntu can read it.

If they were burned in Windows the best program to use to burn CD's/DVD's and have them work in Ubuntu is CDBurnerXP. Just google "CDBurnerXP" and the website should be one of the first reults displayed.

---

### Post by DrDevice on 2009-07-27
Try going to a terminal and typing```
sudo mount /media/cdrom
``` and see what it says there.  If it's an error, post the results and the contents of your /etc/fstab please. :)

---

### Post by amarumayo on 2009-07-27
Thanks for the reply
When I run sudo mount /media/cdrom it says:
No medium found on /dev/sr0

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c3c4608e-fb99-4989-bfe2-ede4aec72b38 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4427a2e3-37e1-437d-9f43-08617e2c7989 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by DrDevice on 2009-07-27
> **amarumayo said:**
> No medium found on /dev/sr0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Your mount command references sr0, your fstab references scd0, hmm..

Try ```
sudo umount /media/cdrom
sudo mount /dev/scd0 /media/cdrom
``` in that order, and reply with what happens.

---

### Post by amarumayo on 2009-07-27
Here is what I get:

christopher@bird-laptop:~$ sudo umount /media/cdrom
umount: /media/cdrom: not mounted
christopher@bird-laptop:~$ sudo mount /dev/scd0 /media/cdrom
mount: /dev/sr0: unknown device
christopher@bird-laptop:~$ 

Thanks

---

### Post by DrDevice on 2009-07-27
OK, after doing some research, I have discovered that sr0 & scd0 are supposedly the same thing.  So that's normal.  What's not normal is the "unknown device".

Try```
ls -l /dev/sr0 /dev/scd0
``` and reply with the results plz. =)

P.S. Also, what brand/model is your drive?

---

### Post by amarumayo on 2009-07-27
OK I got:

christopher@bird-laptop:~$ ls -l /dev/sr0 /dev/scd0
lrwxrwxrwx  1 root root      3 2009-07-27 08:41 /dev/scd0 -> sr0
brw-rw----+ 1 root cdrom 11, 0 2009-07-27 08:41 /dev/sr0
christopher@bird-laptop:~$ 

Not sure how to find out what the make and model of my DVD drive is.
I have to go to work so I will subscribe to this thread and check back later.  
Thanks

---

### Post by DrDevice on 2009-07-27
Cool, that's what I have on mine, so that's all set right.  scd0 seems to be a link to sr0, probably for legacy support.

Hokay, let's try one more mount command:```
mount /dev/scd0 /media/cdrom -t udf
```

That should force the mount command to mount the DVD in the right place, with the right filesystem.  Please reply with the results, of course.

If that doesn't solve the problem, then I'm not sure where it's going haywire.  As far as I can tell, all your settings are correct.  The reason I asked about your drive make/model is that it's possible you're using an IDE DVD drive, whereas Ubuntu is trying to use it as a SCSI drive.  If you're using a SATA or a SCSI drive, that's fine, but IDE should be something like /dev/hd*something*.

Sorry I couldn't be of more help!

---

### Post by amarumayo on 2009-07-27
Works!!!!

Thanks a ton,
CHris

---

### Post by DrDevice on 2009-07-30
Glad to hear it!  UDF is for DVD's, ISO9660 is for CD-ROMs, FYI.

Just to keep things clean, I'd run ```
gksu gedit
``` and open /etc/fstab, then remove the line for your CD-ROM ```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```.  You'll still have to mount manually, but it's just one less thing for your computer to worry about during boot.  It may also fix the auto-mounting as well, but I can make no claims or guarantees on that. :)

Cheers, mate, and have fun with Ubuntu!

---

### Post by ShortE on 2009-08-14
I have an Acer Aspire 4810TZ-4011 and I just tried all of these commands and still got :

abbi@CharlieII:~$ sudo mount /dev/scd0 /media/cdrom
mount: /dev/sr0: unknown device
abbi@CharlieII:~$ ls -l /dev/sr0 /dev/scd0
lrwxrwxrwx  1 root root      3 2009-08-14 22:22 /dev/scd0 -> sr0
brw-rw----+ 1 root cdrom 11, 0 2009-08-14 22:22 /dev/sr0
abbi@CharlieII:~$ mount /dev/scd0 /media/cdrom -t udf
mount: only root can do that
abbi@CharlieII:~$ sudo mount /dev/scd0 /media/cdrom -t udf
mount: no medium found on /dev/sr0
abbi@CharlieII:~$ 

So still no media found.  Any other suggestions Ubuntu community?

---

### Post by shagbark on 2009-08-16
I have an ASRock AOD790GX/128M with an AMD dual-core X2.
Same exact problem.  And I can't receive any software updates, because the software updater won't update any other package information because it can't read my cd-rom, which it shouldn't even be checking for package updates anyway.

$ sudo mount /dev/scd0 /media/cdrom
mount: /dev/sr0: unknown device
$ ls -l /dev/sr0 /dev/scd0
lrwxrwxrwx  1 root root      3 2009-08-15 16:35 /dev/scd0 -> sr0
brw-rw----+ 1 root cdrom 11, 0 2009-08-15 16:35 /dev/sr0
$ sudo mount /dev/scd0 /media/cdrom -t iso9660
mount: no medium found on /dev/sr0

---

### Post by ambawatajay on 2009-08-25
Even I am facing the same issue.
Can't mount any Disc, whether CD/VCD/DVD.
Always says "mount: no medium found on /dev/sr0":confused:
Any solution ?:(

---

### Post by acpride on 2009-10-24
Same problem here :(

Ubuntu 9.04 installed in a brand new Acer aspire 5810T laptop. Impossible to mount any kind of cd or dvd, i got the same message "no medium found on /dev/sr0"

The ls command shows the same information as the others in this thread:

```
lrwxrwxrwx  1 root root      3 2009-10-24 12:28 /dev/scd0 -> sr0
brw-rw----+ 1 root cdrom 11, 0 2009-10-24 12:28 /dev/sr0

```The fstab cdrom line is the same too:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

In dmesg command I found this:

```
[   20.450130] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GU10N     AP03 PQ
```

It seems that the drive is recognized, but can't be mounted. 

I'm really stuck here.

---

### Post by spennine on 2009-11-05
same here.
dmesg | grep sr0
[    2.746798] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.746862] sr 4:0:0:0: Attached scsi CD-ROM sr0


dmesg | grep LITE
[    1.852459] ata5.00: ATAPI: LITE-ON DVDRW LH-20A1H, LL06, max UDMA/66
[    2.741701] scsi 4:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL06 PQ: 0 ANSI: 5

uname -r
2.6.31-14-generic

9.10 - the Karmic Koala

all updates applied...

the eject command works.

one thing to note with this install;  the CD/DVD device was installed after the OS was installed on the box.  so the install took place with no available CD/DVD device.  I wonder if it built my kernel differently because of that (IE, no cdrom, ide-cd, ide-scsi module available.)

I've tried modprobe on cdrom, ide-cd, ide-scsi, and all return FATAL: Module <module_name> not found.

thankfully I have another Ubuntu install (V8) that does recognize the CD/DVD device...

---

### Post by berilac on 2009-12-19
Seems I have the same problem. 

Can play audio CD's, but not (it appears to be CSS) dvd's...

Have read about this in so many places now, and they are all unresolved.
There is little point in me posting dmesg, etc, etc...my results are much the same as above...but I will if you ask.

Running Ubuntu Karmic 9.1 (latest kernel headers 2.6.32...)

Any ideas???


FOR REFERENCE:

please see here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446612](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446612)

As far as I'm aware this is the same problem (quite specifically) - And as of yet, no solution....

FURTHER EDIT:

It seems that my problem is worse than I thought. Ubuntu won't even recognise blank DVD - so I guess it's not CSS issue...(but then, I'm not sure if this is a DVD writer - so that could explain that one)

Also, it appears to be with home written dvd's too - not just CSS...

Have just double-checked with CD, and they mount fine (including blank cd).

Have no idea what's going on...!

---

### Post by mathspeedy on 2009-12-20
Hi! I can't say why but my optic drive decided to stop recognizing DVDs (CD works)
:(

---

### Post by Bobhuber on 2010-01-09
Karmic 9.10 fresh install. Same problem ANY FIX YET ??

---

### Post by Zundap on 2010-01-09
I get that same message when i try to acces a disc in the drive, but my drive wont even open now, i assumed that DVD player/writer had gone down, i was going to try fitting a new dvd drive, but after reading this post, it rather looks as though it could be another ubuntu problem. Ile follow this thread with interest.

I am running ubuntu 9.04 though.

---

### Post by boombox1387 on 2010-07-18
Sorry to bring up an old thread, but this definitely doesn't seem to be resolved for many people, myself included.  I'm having this problem with 10.04, and I've had it for at least the past year with Ubuntu, maybe more.  The drive works fine during boot and with Windows XP, so this is definitely an Ubuntu issue.

Has anyone found a solution?  or at least filed a bug report?

---

### Post by Bobhuber on 2010-07-18
> **boombox1387 said:**
> Sorry to bring up an old thread, but this definitely doesn't seem to be resolved for many people, myself included.  I'm having this problem with 10.04, and I've had it for at least the past year with Ubuntu, maybe more.  The drive works fine during boot and with Windows XP, so this is definitely an Ubuntu issue.

Has anyone found a solution?  or at least filed a bug report?
There is a program called GnomeBaker that will allow you to write to a blank RW/DVD without mounting it first.Once data is written to the disk the other programs seem to then recognize the drive. Definitely not a fix for the bug but a workaround. File another bug report and maybe if they get enough of them they will realize there is indeed a problem.

---

### Post by ameseisch on 2011-01-20
I am in the same boat. Haven't been able to solve. This is one of 4 machines I have running Ubuntu and the only one I have ever had a problem with as far as the cd/dvd drives go.

---

### Post by ameseisch on 2011-01-20
I am in the same boat. Haven't been able to solve. This is one of 4 machines I have running Ubuntu and the only one I have ever had a problem with as far as the cd/dvd drives go.

---

### Post by enever on 2011-05-09
I have exactly the same problem but with a slight twist. If I reboot the laptop (Acer Aspire 5810) with a cd or dvd in the drive it mounts and can be played. If I remove it from the drive and insert another disc I revert to the original issue.
As an experiment, when I upgraded to 11.04 I left a disc in the drive in the hope that it would force the drive to be installed correctly. Unfortunately it didn't work.
I also tried "mount /dev/scd0 /media/cdrom -t udf" but all I get is the response "mount: only root can do that".
As with everyone else, the drive is working fine under Windows. This issue has been going on for far too long and, whilst it is not too big a deal for me to reboot, it should be fixed by now. 11.04 has some great features but I can hardly sing its praises if something as basic as a cd/dvd drive doesn't work "out of the box".

---

### Post by Mash909 on 2011-05-15
Same problem on 10.10
2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 
```

# mount /dev/scd0 /media/cdrom
```

returns 


```
mount: no medium found on /dev/sr0
```

I've checked for iso9660 compatibility.
I can read data from other CDs fine.

---

### Post by Mash909 on 2011-06-28
Looks like I'm affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544")

---

