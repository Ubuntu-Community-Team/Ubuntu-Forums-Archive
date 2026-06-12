---
title: "New Computer, DVD not working right!"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by myolbug on 2009-03-14
I have this:[http://www.tigerdirect.com/applicati...SYXS-BB-981155](http://www.tigerdirect.com/applicati...SYXS-BB-981155)
Systemax No O/S AMD Desktop PC - AMD Athlon 64 X2 4400+, 3GB DDR2 800MHz, 250GB SATA II, 20X DVD-RW Just got it today. Ubuntu 8.10 64 on it.

I cannot get the DVD player to work. I know it reads, it shows the title of whatever I put into it, but it just won't play.
Movie Player says resource not found. If I go into Movie>Play Disc 
What say you?

---

### Post by taurus on 2009-03-14
If it's a movie DVD, then you need to install libdvdcss2 first though.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by abn91c on 2009-03-14
> **taurus said:**
> If it's a movie DVD, then you need to install libdvdcss2 first though.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
+1 for this guide, I just got my dragon player working finally on my Inspiron 1000 Laptop's DVD drive. :)

---

### Post by myolbug on 2009-03-14
No dice.  Maybe the drive is bad?  It plays everything else, though.  Anyone else?

---

### Post by coolbrook on 2009-03-14
Try MPlayer for watching DVDs.  It's in the repositories.

---

### Post by myolbug on 2009-03-15
Okay I installed MPayer, but it gives me the error message window of: ERROR!
MPEG: Mising Video Stream!?  Contact the author, it may be a bug:(

What now?

---

### Post by myolbug on 2009-03-15
When I try it in Movie Player Xine it asks me if I am trying to play it without Libdvdcss.  I have this.

---

### Post by mc4man on 2009-03-15
For totem-xine you also need libxine1-ffmpeg installed

You could also put the dvd in the drive and run this fron terminal to ck. on the mount point, /dev/ links and if the file system is mounted properly (look for *cdrom entry
```

sudo lshw -C disk
```

---

### Post by abn91c on 2009-03-15
did you install ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by myolbug on 2009-03-15
> **mc4man said:**
> For totem-xine you also need libxine1-ffmpeg installed

You could also put the dvd in the drive and run this fron terminal to ck. on the mount point, /dev/ links and if the file system is mounted properly (look for *cdrom entry
```

sudo lshw -C disk
```

*-cdrom                 
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-disk
       description: ATA Disk
       product: Hitachi HDP72502
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: GM2O
       serial: GEK234RHR3607A
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000e1723

---

### Post by teamcoltra on 2009-03-15
> **abn91c said:**
> did you install ```
sudo apt-get install ubuntu-restricted-extras
```

^ Please put the above in terminal you should than be a very happy person.

---

### Post by myolbug on 2009-03-15
> **teamcoltra said:**
> ^ Please put the above in terminal you should than be a very happy person.


I have and there is no change.  Same error messages

---

### Post by mc4man on 2009-03-15
Install regionset ```
sudo apt-get install regionset
```

Then with a dvd in the drive run
```
regionset
```
If you see this in the line type: 
type: none

Then set it to your region (1- N america, 2- europe, anywhere else say where your from.

You'll only need to set it once, don't keep changing (only 5 resets in total allowed.

Edit;

If you didn't have a region set and after setting if the same dvd still doesn't work, then go into home folder, find the .dvdcss folder and delete it. (it will be rebuilt next dvd you try to play

.dvdcss is a hidden folder, if not visible go Ctrl+h on your keyboard while in home folder

Also for info -  your lshw came up fine, the drive mounts at /media/cdrom0, with a dvd /dev link of /dev/dvd and the media (your dvd) was mounted correctly

---

### Post by myolbug on 2009-03-15
I went into the home folder and did a search.  In system I found libbrasero-dvdcss.la and libbrasero-dvdcss.so.  The icons for them are pieces of paper and the .la one has a diamond shape on it.  They both have a lock icon above them,

I have admin rights, but should I try this as root?  Without the search I didn't find any .dvdcss, though I didn't go into ea. folder.  If I need to do this as root, how do I do this?

---

### Post by myolbug on 2009-03-15
I noticed that you said I should delete the folder, but I cannot find a *folder* that says .dvdcss.

---

### Post by taurus on 2009-03-15
> **myolbug said:**
> I noticed that you said I should delete the folder, but I cannot find a *folder* that says .dvdcss.

It's a hidden directory.

```
ls -la ~
```

---

### Post by myolbug on 2009-03-15
This gave me a list of files in the terminal, but none of them were dvdcss 
Sorry, still a bit of a noob to all of this.  Do I need to post the list?

---

### Post by taurus on 2009-03-15
If you want to.  Either you have one, .dvdcss, or you don't.

---

### Post by myolbug on 2009-03-15
Okay, lets say I don't.  What should I do then?

---

### Post by djbushido on 2009-03-15
Installing dvdcss doesn't actually install this.
Do "sudo apt-get install libdvdread3"
then do "sudo /usr/share/doc/libdvdread3/install-css.sh"
this will install dvdcss.
instructions taken from [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by myolbug on 2009-03-15
SUCCESSSSSS!!!:D

This is what I needed.  I already had libdvdread 3 but it wasn't installed!!  Thanks so much!

---

### Post by Jeztastic on 2009-04-05
Fixed it for me too, but Totem still didn't want to play the DVD, so used VLC instead.

---

