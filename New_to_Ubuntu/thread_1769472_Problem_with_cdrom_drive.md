---
title: "Problem with cdrom drive"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by Linux_buddy on 2011-05-28
Hi, 
   I am currently using Ubuntu 11.04. Mine is LG XNOTE. My problem is that the computer doesn't detect my CDROM when i insert a CD. It even not showing the icon for the cdrom. No problem with the Hardware,i have checked it in the windows. I have read many posts regarding this in the forum. But NONE of them have fixed the problem.Plz help me.

---

### Post by Jedibart on 2011-05-28
Same here, it's like Ubuntu turned it off when it loads, because the disk doesn't spin up or anything. 
It's the CDROM drive that I loaded Ubuntu off of, so I know it works!

sudo lshw -c disk yeilds:  (only CD part shown)

  *-cdrom                 
       description: DVD writer
       product: DVD+-RW DVD8631
       vendor: PHILIPS
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CD21
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

---

### Post by Jedibart on 2011-05-28
Ok, I think I've got it:

The CDROM is a CD AND a dvd, mounting the CD doesn't work, but this seems to clear everything up:

sudo mount /dev/dvd /cdrom

---

### Post by Linux_buddy on 2011-06-05
This is what it gives,

 ```
sudo mount /dev/dvd /cdrom

 mount: /dev/sr0: unknown device

```

---

