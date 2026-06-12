---
title: "Cannot Mount DVD drive/burner"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Laroeri on 2010-08-09
Hello,

I have an LG DVD drive but cannot mount it... Since I am fairly new at the great Linux world (on Ubuntu 10.04) I need some help...

Thanking you in advance...:popcorn:

---

### Post by greenwom on 2010-08-09
I'm assuming this is a usb burner.

If so check that it is being seen by the system,  

Try the "lsusb" command and "dmesg | tail"

If it's usb, does it have power.  If so but a disc in, then try to mount.
It will not show up without a disc, at least in my experiance.

Hope I'm not off base with it being usb.

---

### Post by Laroeri on 2010-08-10
Thanks for the reply,

It is not a USB drive. And I tried putting a disk in but it still won't mount it. The disk spins and therefor there is power but yet, I can't mount the drive to go see what's on it or to burn any data...

As I said I am fairly new at this... Let me know if you need more infos before proposing any technique...

Thanks again:KS

---

### Post by greenwom on 2010-08-10
Ok goto the places tab in the menu.  
Is there a CD drive listed?

Try this 

go to a terminal 
```
Applications --> Accessories -- Terminal
```
Type
```
cd /dev
```
Then type ```
ls
```
and you should have a large list.  Look for cdrom or dvd entries

then go ```
sudo mkdir /media/cdrom5
```
I use the #5 so you can remember that you made this mount point.  The system may already have mount points, but we'll make our own.
This will ask for you root password.  Go ahead.

then type ```
sudo mount /dev/cdrom /media/cdrom5
```

if the drive is there this should mount it. 
If not I'm at a bit of a loss, not being there.  
I'd check the cables from the drive to board or check BIOS to see if it's disabled.

---

### Post by Laroeri on 2010-08-10
Hello again,

That was sure fast... I tried what you said. Most of it worked but not the end...

```
 then go      
Code:     sudo mkdir /media/cdrom5 I use the #5 so you can remember that you made this mount point.   
The system may already have mount points, but we'll make our own.
This will ask for you root password.  Go ahead.

```That worked

```
then type      Code:
     sudo mount /dev/cdrom /media/cdrom5
```

It took a while but I was told that it was an unknown peripheral (excuse my translation but my system is in French)

I double checked if it was plugged and it seems to be so...

I was wondering if it would be the same procedure since it is an internal DVD burner and the command called for a cdrom

Thanks again

---

### Post by greenwom on 2010-08-10
in your /dev folder you will have referance to /dev/dvd as well.
you can try the same command with dvd instead of cdrom.

Sounds like you have something else going on here to me.

---

### Post by cavalier911 on 2010-08-10
Open terminal:
```
wodim --devices
```This should output the actual device name for your optical drive not a shortcut.
Mine returns /dev/scd0 but yours could be different:
```
rj@intrepid:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'    rwrw-- : 'TSSTcorp' 'CDDVDW SH-S223F'
-------------------------------------------------------------------------

```Put a data cd or dvd (NO audiocd)in drive:
```
sudo mount -t iso9660 /dev/from.wodim   /media/cdrom5
```In ubuntu gnome when you successfully mount an optical disk where the mount folder is in /media an icon appears on the desktop.Clicking the icon will launch nautilus file manager with contents of mounted cd showing.

---

### Post by retter on 2010-08-10
I'm having a similar problem, but my drive won't even open.  There is no dvd or cd drive in /dev.  "wodim --devices" returns:

wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

I have a blu ray/cddvdrw combo drive.  Any suggestions?

---

### Post by greenwom on 2010-08-10
> **cavalier911 said:**
> Open terminal:
```
wodim --devices
```This should output the actual device name for your optical drive not a shortcut.
Mine returns /dev/scd0 but yours could be different:
```
rj@intrepid:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'    rwrw-- : 'TSSTcorp' 'CDDVDW SH-S223F'
-------------------------------------------------------------------------

```Put a data cd or dvd (NO audiocd)in drive:
```
sudo mount -t iso9660 /dev/from.wodim   /media/cdrom5
```In ubuntu gnome when you successfully mount an optical disk where the mount folder is in /media an icon appears on the desktop.Clicking the icon will launch nautilus file manager with contents of mounted cd showing.


Thanks for that info...  I've never run into this problem before, glad someone can help Laroeri with his problem

---

### Post by Laroeri on 2010-08-11
Thank you both,

When I did what greenwom said, here's what I got

```
papa@filles-desktop:~$ sudo mkdir /media/dvd5
papa@filles-desktop:~$ sudo mount /dev/dvd /media/dvd5
mount: /dev/sr0: périphérique inconnnu
```So I kept ion reading and got

```
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'    rwrw-- : 'HL-DT-ST' 'DVD-RAM GSA-H22N'
 1  dev='/dev/scd1'    rwrw-- : 'HL-DT-ST' 'CD-RW GCE-8523B'
-------------------------------------------------------------------------
```Seems like we're getting somewhere since the drive seems to be able to read at least the name of the disk :D but I can't see what is on it... :(

With a disk like a Ubuntu 9,10 installation DVD (data) in the DVD-RAM drive, I get a message box telling me (file attached)

```
Error mounting: block device /dev/sr0 is write protected, mounting read-only
mount: /dev/sr0: can't read superblock
```And for the rest

```
sudo mount -t iso9660 /dev/from.wodim   /media/cdrom5
```I am not sure what to adjust... As I said earlier, I'm still learning English and Linux... 

I'll stay posted...

Thanks again :popcorn:

---

### Post by cavalier911 on 2010-08-11
>      Code:
     wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='[COLOR=Magenta]/dev/scd0[/COLOR]'    rwrw-- : 'HL-DT-ST' 'DVD-RAM GSA-H22N'
 1  dev='[COLOR=Red]/dev/scd1[/COLOR]'    rwrw-- : 'HL-DT-ST' 'CD-RW GCE-8523B'
------------------------------------------------------------------------- 
Put CD/DVD disk in 'CD-RW GCE-852-8523B' drive

Mount with this command:

```
sudo mount -t iso9660 [COLOR=Red]/dev/scd1[/COLOR] /media/cdrom5
```or 

Put CD/DVD disk in 'DVD-RAM GSA-H22N' drive

Mount with this command:

```
sudo mount -t iso9660 [COLOR=Magenta]/dev/scd0[/COLOR] /media/cdrom5
```This shouldn't be necessary, but it's good to know how.
Ubuntu should automount when you put a disk in the drive.
Try another disk if you get the read failure.

---

### Post by frenchn00b on 2010-08-11
I have a script for that ( if fstab is well configured)

```

if [ "$1" = "-mountcd" ] ; then
        eject -t
        CDWOD=`wodim --devices | grep  dev= | cut -f1 | cut -d"=" -f2  | sed s/\'//g | tail -n 1 `
        echo "$CDWOD detected"
        mount $CDWOD
        echo "$(date) $MSG"
        mount 
        notify-send "The CD-ROM is at  /media/cdrom !!"
        notify-send "The CD-ROM is at  /media/cdrom !!"
        exit
        exit 0
fi

if [ "$1" = "-umountcd" ] ; then
        #CDWOD=`wodim --devices | grep  dev= | cut -f1 | cut -d"=" -f2  | sed s/\'//g | tail -n 1 `
        #echo "$CDWOD detected"
        #mount $CDWOD
        echo "$(date) $MSG"
        mount 
        eject
        exit
        exit 0
fi




```

---

### Post by Laroeri on 2010-08-11
So I tried what Cavalier911 said and it didn't work. 

And tried to copy and paste the script that frenchn00b said in the Terminal window (was it there I was supposed to?) and each time, it would close the window.

I noticed after doing these two procedures that when I put a CD in the 
1  dev='[COLOR=Red]/dev/scd1[/COLOR]'    rwrw-- : 'HL-DT-ST' 'CD-RW GCE-8523B

in the shortcuts I get two lines for the same CD. So When I put the Ubuntu CD in, it said Ubuntu 10.04 and cdrom5. When I clicked on the first one, it said it couldn't read superblocks and that it was in the read only mode. When I clicked on the second, it gave me everything I had on the CD.

I tried the same for the 
0  dev='[COLOR=Magenta]/dev/scd0[/COLOR]'    rwrw-- : 'HL-DT-ST' 'DVD-RAM GSA-H22N'
 
But it would simply reply 
Error mounting: block device /dev/sr0 is write protected, mounting read-only
mount: /dev/sr0: can't read superbloc

So maybe I did not do the procedure well.n Or I wasn't supposed to paste it in the Terminal window ?

Still need your guidance ...

Thanks in advance:?

---

### Post by Laroeri on 2010-08-13
Hello again,

I dare to ask for some help again... :(

Thank you so much for your time and advice...:KS

---

### Post by Laroeri on 2010-08-17
> **frenchn00b said:**
> I have a script for that ( if fstab is well configured)

```

if [ "$1" = "-mountcd" ] ; then
        eject -t
        CDWOD=`wodim --devices | grep  dev= | cut -f1 | cut -d"=" -f2  | sed s/\'//g | tail -n 1 `
        echo "$CDWOD detected"
        mount $CDWOD
        echo "$(date) $MSG"
        mount 
        notify-send "The CD-ROM is at  /media/cdrom !!"
        notify-send "The CD-ROM is at  /media/cdrom !!"
        exit
        exit 0
fi

if [ "$1" = "-umountcd" ] ; then
        #CDWOD=`wodim --devices | grep  dev= | cut -f1 | cut -d"=" -f2  | sed s/\'//g | tail -n 1 `
        #echo "$CDWOD detected"
        #mount $CDWOD
        echo "$(date) $MSG"
        mount 
        eject
        exit
        exit 0
fi




```
I haven't been usin Ubuntu for a long time so I was wondering where do I copy this script ?

Thanks !

---

### Post by Braik on 2010-08-17
Hi everybody,
 
Well I am having trouble to mount dual layer DVD on my computer, since all other kind of medias are accepted and auto mounted.
 
I have verified that with 2 dual layer backup films made with M$ win.
 
Is there any way to mount these?
 
PS. I have also tried to put a blank dual layer DVD and it does not recognise my DVD, whîle other CD and DVD are automatically mounted (blank, backup and original)
 
Please help,
 
Thanks

---

### Post by Braik on 2010-08-18
bump

---

### Post by Laroeri on 2010-08-22
What does the bump mean ?

Should I expect an answer or get desperate...:(

---

### Post by Rifester on 2010-08-22
This is a known bug...  The only way I could get Lucid to recognize blank DVD was with K3B.   For whatever reason it recognizes blank DVD while Brasero wil not.

---

### Post by chips24 on 2010-08-22
Are you using ext4 for your hard disk? Ubuntu can not mount drives on ext4.

---

### Post by clhsharky on 2010-08-23
> Ubuntu can not mount drives on ext4
Yes you can.
Install release 9.10 or newer on ext4 and it will mount other ext4 partition and hard drives.

Sharky

---

### Post by Braik on 2010-08-24
Hi,
 
Well, in my case I have Lucid (10.04) and YES my entire system is in ext4 (99% sure). And the main problem is that it only do not recognize Dual Layer DVD's blank or not blank.
 
Is there any way to fix this?
 
Thanks

---

### Post by Laroeri on 2010-08-29
So now my DVD drive will see that there is a DVD and read it. But it won't read or play any video...

What can I do ?

Please...:(

---

### Post by Laroeri on 2010-09-15
Hello 

Is anyone out there ?  ](*,)

I could really use some help.

Thanks in advance

---

### Post by Braik on 2010-09-16
Hi Laroeri,
 
Well, don't be desperate, just follow this instructions
 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
 
This is the main Thread of the multimedia forum, it is supposed let you read (almost?) all multimedia content on all variants of Ubuntu. I think it is the best guide you can follow.
 
Good luck
 
Braik

---

### Post by Heaphy on 2012-05-27
Hi, I'm having issues with my DVD drive too and not sure how to fix it.
I am also a bit new to the wonderful world of linux - running ubuntu 12.04

I have tried following the instructions on this thread but it seem fruitless for me.

When typing in
[code] wodim --devices [code]

I ended up recieving this message.
[code] heaphy@heaphy-Not-Specified:~$ wodim --devices
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation. [code]

Also when previously typing in: cd /dev and then: ls
I got the following...
[code] heaphy@heaphy-Not-Specified:~$ cd /dev
heaphy@heaphy-Not-Specified:/dev$ ls
agpgart          net                 sdb1      tty24  tty57      ttyS30
autofs           network_latency     sdb2      tty25  tty58      ttyS31
block            network_throughput  sdb5      tty26  tty59      ttyS4
bsg              null                sdb6      tty27  tty6       ttyS5
btrfs-control    oldmem              sdc       tty28  tty60      ttyS6
bus              parport0            sdc1      tty29  tty61      ttyS7
char             port                sdd       tty3   tty62      ttyS8
console          ppp                 sdd1      tty30  tty63      ttyS9
core             psaux               sg0       tty31  tty7       uinput
cpu              ptmx                sg1       tty32  tty8       urandom
cpu_dma_latency  pts                 sg2       tty33  tty9       usbmon0
disk             ram0                sg3       tty34  ttyprintk  usbmon1
dri              ram1                shm       tty35  ttyS0      usbmon2
ecryptfs         ram10               snapshot  tty36  ttyS1      usbmon3
fb0              ram11               snd       tty37  ttyS10     usbmon4
fd               ram12               stderr    tty38  ttyS11     usbmon5
fd0              ram13               stdin     tty39  ttyS12     v4l
full             ram14               stdout    tty4   ttyS13     vcs
fuse             ram15               tty       tty40  ttyS14     vcs1
hpet             ram2                tty0      tty41  ttyS15     vcs2
input            ram3                tty1      tty42  ttyS16     vcs3
kmsg             ram4                tty10     tty43  ttyS17     vcs4
log              ram5                tty11     tty44  ttyS18     vcs5
loop0            ram6                tty12     tty45  ttyS19     vcs6
loop1            ram7                tty13     tty46  ttyS2      vcsa
loop2            ram8                tty14     tty47  ttyS20     vcsa1
loop3            ram9                tty15     tty48  ttyS21     vcsa2
loop4            random              tty16     tty49  ttyS22     vcsa3
loop5            rfkill              tty17     tty5   ttyS23     vcsa4
loop6            rtc                 tty18     tty50  ttyS24     vcsa5
loop7            rtc0                tty19     tty51  ttyS25     vcsa6
loop-control     sda                 tty2      tty52  ttyS26     vga_arbiter
lp0              sda1                tty20     tty53  ttyS27     video0
mapper           sda2                tty21     tty54  ttyS28     zero
mcelog           sda5                tty22     tty55  ttyS29
mem              sdb                 tty23     tty56  ttyS3
[code]


Any ideas of how to help?

---

### Post by Sef on 2012-05-27
Back to sleep. Necromancing.

---

