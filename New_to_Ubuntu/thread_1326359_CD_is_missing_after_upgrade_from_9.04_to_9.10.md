---
title: "CD is missing after upgrade from 9.04 to 9.10"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by shortrun on 2009-11-14
I do not see the CD after upgrading.  I goto   Places - Computer  and I only see the File System.

It was there before the upgrade.  I upgraded after being prompted by Ubuntu.  So I didn't download and install 9.10 from a CD or USB jumpdrive.  I just let it happen over the internet.

I did notice if I'm looking at the screen   Places - Computer  and push the door open button on the actual CD drive, then the CD icon appears.  ??    Then the icon disappears as soon as the CD goes back into it's normal state (sucks the CD back inside the chassis) (sorry for the no tech description) .

I have read where others have had similar problems too.

Help please.

---

### Post by The Funkbomb on 2009-11-14
Try this...

cd /dev/ &&ls

Do you see your cdrom in there?

---

### Post by shortrun on 2009-11-14
This is what I see when I goto the terminal and enter.   cd /dev/ &&ls

I'm quite new to ubuntu and linux, so I'm not sure what should be there


brian@brian-desktop:~$ cd /dev/ &&ls
adsp             mapper              ram6        tty12  tty4   ttyS0
agpgart          mcelog              ram7        tty13  tty40  ttyS1
audio            mem                 ram8        tty14  tty41  ttyS2
binder           mixer               ram9        tty15  tty42  ttyS3
block            net                 random      tty16  tty43  urandom
bus              network_latency     rfkill      tty17  tty44  usbmon0
cdrom1           network_throughput  rtc         tty18  tty45  usbmon1
char             null                rtc0        tty19  tty46  usbmon2
console          nvidia0             scd0        tty2   tty47  usbmon3
core             nvidiactl           sda         tty20  tty48  vcs
cpu_dma_latency  oldmem              sda1        tty21  tty49  vcs1
disk             parport0            sda2        tty22  tty5   vcs2
dsp              pktcdvd             sda5        tty23  tty50  vcs3
ecryptfs         port                sequencer   tty24  tty51  vcs4
fd               ppp                 sequencer2  tty25  tty52  vcs5
full             psaux               sg0         tty26  tty53  vcs6
fuse             ptmx                sg1         tty27  tty54  vcs7
hpet             pts                 shm         tty28  tty55  vcs8
input            ram0                snapshot    tty29  tty56  vcsa
kmsg             ram1                snd         tty3   tty57  vcsa1
log              ram10               sndstat     tty30  tty58  vcsa2
loop0            ram11               sr0         tty31  tty59  vcsa3
loop1            ram12               stderr      tty32  tty6   vcsa4
loop2            ram13               stdin       tty33  tty60  vcsa5
loop3            ram14               stdout      tty34  tty61  vcsa6
loop4            ram15               tty         tty35  tty62  vcsa7
loop5            ram2                tty0        tty36  tty63  vcsa8
loop6            ram3                tty1        tty37  tty7   zero
loop7            ram4                tty10       tty38  tty8
lp0              ram5                tty11       tty39  tty9
brian@brian-desktop:/dev$

---

### Post by The Funkbomb on 2009-11-14
Okay.

Next thing I want you to do is type:

```
sudo gedit /etc/fstab
```

This will open the text editor.  Let's make sure that the CD drive is being mounted.

Near the bottom, it should say something like:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Yours may be different.  Copy and paste that line here.

---

### Post by shortrun on 2009-11-14
I have follow the instruction and get -

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

and expected

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I noticed this says  "cdrom0"  and in my post above of my directory it is "cdrom1"
?? does this mean anything ??

---

### Post by shortrun on 2009-11-14
I should note that I do have a audio CD in the player.

Still looking for a solution.  Thanks much tor the responses so far.

See below

brian@brian-desktop:/dev$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: WDC WD1200BB-00G
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 08.0
       serial: WD-WMALK1368864
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0008031e
  *-cdrom
       description: SCSI CD-ROM
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio
       configuration: status=ready

---

### Post by shortrun on 2009-11-16
Ok
I put the cd in the cdrom to reinstall 9.04.
Now I see the CD and it appears normal.
I still see nothing when an audio CD is put in.
So it looks like it's not the cdrom or related software.  Something to do with audio cd's  ??

---

### Post by shortrun on 2009-11-18
Ok it's solved, thanks to Youtube
I went to    -Applications   -Ubuntu software centre   - search for   Exaile

I installed this ran it  then   select disk
and the CD began to play.

---

