---
title: "DVD does not mount"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by dubhear on 2008-12-30
> **albinootje said:**
> Did you install the libdvdcss2 package ?
See the Medibuntu repositories howto :
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) [/thread]

---

### Post by Michael.Godawski on 2008-12-30
> **dubhear said:**
> most of the times when i try to use my dvd:s
system says E: unable to mount

so what is really going on here
i'm absolutely sure some one can help, and my hardware seems to be just fine

cannot burn dvd's, but cd:s works just fine

i have two dvd-drives in use.

both made by LG

thanks for reading this far

------------------------------------------------------------------------------------------------

I'll post some screenshots tomorrow

any help would be greatly appreciated

hi,

can you please post the output of

```
sudo lshw -C disk
```Perhaps you have to enable the support for restricted formats; run this in terminal:
```

 sudo apt-get install libdvdread3 gstreamer0.10-plugins-ugly
``````
 sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by dubhear on 2008-12-31
*-disk                  
       description: ATA Disk
       product: WDC WD2500JS-00N
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 10.0
       serial: WD-WCANK3608732
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=301524ab
  *-disk
       description: ATA Disk
       product: Maxtor 6Y160P0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y60NX1CE
       size: 152GiB (163GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f7a19649
  *-cdrom:0
       description: DVD-RAM writer
       product: DVDRAM GSA-4040B
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: A301
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD reader
       product: RW/DVD GCC-4320B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/CHARLES_CHAPLIN_LIFE_AND_ART
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/CHARLES_CHAPLIN_LIFE_AND_ART
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted

---

### Post by dubhear on 2009-01-06
seems like I still can't mount empty dvd's

but i can watch some  i have both empty dvd + and -
neither did work

so do i sudo chown -R /dev

---

### Post by oldos2er on 2009-01-06
> **dubhear said:**
> so do i sudo chown -R /dev

 You'll likely break your system if you do that. 

 Check System, Administration, Users and Groups, and make sure your username is allowed CD-ROM drive access.

---

### Post by dubhear on 2009-01-06
> **oldos2er said:**
> You'll likely break your system if you do that. 

 Check System, Administration, Users and Groups, and make sure your username is allowed CD-ROM drive access.



done... it's there, was there before i even checked.

what is this /media-folder  could this be malfunctioning...

and for the record, i use gnome baker dvd-burner

should i see if there is blank dvd in my drive, i think i saw that with blank cd?!?

> **stchman said:**
> Install K3b or use Brasero.

```
sudo apt-get -y install k3b libk3b2-extracodecs
```

so should i do that now? i think i will. see if it helps

---

### Post by dubhear on 2009-01-06
[[IMG]http://img525.imageshack.us/img525/285/screenshotcg9.th.png[/IMG]](http://img525.imageshack.us/my.php?image=screenshotcg9.png)
[[IMG]http://img511.imageshack.us/img511/1444/screenshot1ir4.th.png[/IMG]](http://img511.imageshack.us/my.php?image=screenshot1ir4.png)

something has come up, what will i do?

what is the best way to get my images for you to see?

---

### Post by oldos2er on 2009-01-06
Your links don't work.

 /media is where removable media such as CDs and DVDs are mounted. Have you tried both your DVD drives? Are they both capable of burning DVDs?

---

### Post by dubhear on 2009-01-06
> **oldos2er said:**
> Your links don't work.

 /media is where removable media such as CDs and DVDs are mounted. Have you tried both your DVD drives? Are they both capable of burning DVDs?

i know my links don't work :confused:
i want to correct the links but i don't know where or how am i supposed to upload them from my desktop!?!

i have at least one dvd writer,for what i can tell just looking my drives and that list earlier

"capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram"

 and tried them both with + and -dvd

---

### Post by albinootje on 2009-01-06
> **dubhear said:**
> seems like I still can't mount empty dvd's


Mounting empty dvds is by default not possible in Linux.
Please post your screenshots as attachments here, or at e.g. [http://imageshack.us](http://imageshack.us)

---

### Post by albinootje on 2009-01-06
> **dubhear said:**
> 
  *-cdrom:1
       description: DVD reader
       product: RW/DVD GCC-4320B
-- cut --
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/CHARLES_CHAPLIN_LIFE_AND_ART
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted

Did you install the libdvdcss2 package ?
See the Medibuntu repositories howto :
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by dubhear on 2009-02-21
> **albinootje said:**
> Did you install the libdvdcss2 package ?
See the Medibuntu repositories howto :
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

ok! so if anyone has the same problem with dvd's do as above then [or before that] do as the first reply says. then you should be able to run all your dvd's with your drive.

thank you both so much...

and thank you for reading my thread, much <3

---

### Post by dubhear on 2009-04-16
how do i get rid of that annoying poll at the beginning :)

any help would be greatly appreciated, i'm worried some might just do what i didn't when i was angry with all this trouble that i have gone trough.

---

