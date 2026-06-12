---
title: "DVD drive will only recognise music cd's"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by a.v.l on 2009-03-24
My DVD drive only recognises music cd's. It will not play data cd's or dvd's or films, whats wrong please?

---

### Post by UbuntuNerd on 2009-03-24
did it work before?

---

### Post by a.v.l on 2009-03-24
> **UbuntuNerd said:**
> did it work before?

No it hasn't worked before.

---

### Post by UbuntuNerd on 2009-03-24
did you ever install any codecs?

---

### Post by oldos2er on 2009-03-24
> **a.v.l said:**
> My DVD drive only recognises music cd's. It will not play data cd's or dvd's or films, whats wrong please?

 A data CD should pop up a Nautilus window, unless you have it configured not to do so.

 To install libdvdcss2, see [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by abn91c on 2009-03-24
If you haven't done so yet ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by diwas on 2009-03-24
I have the same problem. But my DVD drive would read only Movies and Music CDs. DATA DVDs which I have burnt myself doesnt read. 

Which DVD drive do you have?

---

### Post by a.v.l on 2009-03-24
> **oldos2er said:**
> A data CD should pop up a Nautilus window, unless you have it configured not to do so.

 To install libdvdcss2, see [http://medibuntu.org/](http://medibuntu.org/)

Just installed medibuntu along with every other codec I've come across, but still the same problem. The dvd's and cd's are read correctly in XP and also in Ubuntu 8.04 on another computer, most odd and frustrating.

Presently with a disk in the drive the disk content is read but clicking on any of the icons which appear fails to open the content and produces a box which tells me the file cannot be read, sometimes it says wrong MIME or cannot read file.

---

### Post by a.v.l on 2009-03-24
> **diwas said:**
> I have the same problem. But my DVD drive would read only Movies and Music CDs. DATA DVDs which I have burnt myself doesnt read. 

Which DVD drive do you have?

I'm sorry I don't know, is there a way of finding out without removing it?

---

### Post by oldos2er on 2009-03-25
> **a.v.l said:**
> Presently with a disk in the drive the disk content is read but clicking on any of the icons which appear fails to open the content and produces a box which tells me the file cannot be read, sometimes it says wrong MIME or cannot read file.

 What types of files are these?

---

### Post by diwas on 2009-03-25
> **a.v.l said:**
> Just installed medibuntu along with every other codec I've come across, but still the same problem. The dvd's and cd's are read correctly in XP and also in Ubuntu 8.04 on another computer, most odd and frustrating.

Presently with a disk in the drive the disk content is read but clicking on any of the icons which appear fails to open the content and produces a box which tells me the file cannot be read, sometimes it says wrong MIME or cannot read file.
You said DVD discs are read correctly in XP? With the same drive?
If yes, there's no need to see the DVD drive number :D

---

### Post by a.v.l on 2009-03-25
> **diwas said:**
> You said DVD discs are read correctly in XP? With the same drive?
If yes, there's no need to see the DVD drive number :D

Using XP on the same computer with the same DVD drive and I find that all CD and DVD disks are read correctly. Movies work fine and data CD's which have mainly jpg and pdf files on them work fine too, so what is it that Ubuntu finds so hard to do, any idea how to fix this please.

---

### Post by llamabr on 2009-03-25
Post the output of:

```
cat /etc/fstab
```

Also, with the disk in, the output of:

```
df
```

Finally, what happens if you open vlc and try to open the disk from the menu?

---

### Post by a.v.l on 2009-03-25
> **llamabr said:**
> Post the output of:

```
cat /etc/fstab
```


-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=251b3377-d0c9-44cb-abff-e03da9ff7779 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=E4701D71701D4BA4 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=bed57349-b574-4c52-b41e-c8e848c8ebe2 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0      




Also, with the disk in, the output of:

```
df
```





-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2            108760008  39518120  67032016  38% /
varrun                  387476       104    387372   1% /var/run
varlock                 387476         0    387476   0% /var/lock
udev                    387476        80    387396   1% /dev
devshm                  387476        12    387464   1% /dev/shm
lrm                     387476     39792    347684  11% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1             41801092  36316696   5484396  87% /media/hda1
/dev/scd0              4510624   4510624         0 100% /media/My Disc


Finally, what happens if you open vlc and try to open the disk from the menu?

It will not open any of the CD content, no message just a blank screen.

---

### Post by mc4man on 2009-03-26
Your fstab is most likely wrong, this line,
> /dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
should probably be 
> /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

and this line
> /dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
should for the moment be commented out
> #/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

you should run this to confirm your drive is /dev/scd0 (plus you haven't mentiones if you have 1 or 2 cd/dvd drives
```
sudo lshw -C disk
```

You also may benefit from cleaning up (resetting) your 70-persistent-cd.rules

If you want to post it (and the lshw...) 1st before editing fstab then go

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by a.v.l on 2009-03-26
> **mc4man said:**
> Your fstab is most likely wrong, this line,

should probably be 


and this line

should for the moment be commented out


you should run this to confirm your drive is /dev/scd0 (plus you haven't mentiones if you have 1 or 2 cd/dvd drives
```
sudo lshw -C disk
```

** Result of: ```
sudo lshw -C disk
```

 *-cdrom
       description: DVD writer
       product: DVDRW SHW-1635S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: YS0B
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

** I just have the one DVD drive.

I'm unsure how to make the other changes you mention, can you advise please? 



You also may benefit from cleaning up (resetting) your 70-persistent-cd.rules

If you want to post it (and the lshw...) 1st before editing fstab then go

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

:confused:

---

