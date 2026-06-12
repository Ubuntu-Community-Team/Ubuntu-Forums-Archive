---
title: "Brasero has error locking drive"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by Nicks Spleen on 2007-06-03
Today when I was trying to copy a cd for the first time in fiesty brasero, my favorite burning program, had this error:

Session starting:
	flags			= 16515 
	media type	= 0
	speed		= 0
	track type		= 9
	track format	= 63
	output		= /home/nick/brasero.toc
Session error : the drive can't be locked (Extracting audio from CD)

I tried running the program from a terminal but it didn't help. Also I checked to see if dma was on:

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

DMA appears to be on, although I have no idea that that last line means. I also tried just burning an audio cd and recived the same error message. Has anybody ran into this problem before or can offer any suggestions on how to fix it??

---

### Post by pixatintes on 2007-06-08
I have the same problem...  :(

---

### Post by Kobalt on 2007-06-11
I've had the same problem trying to burn Ogg files to a CD, after a reboot it worked like a charm though...

---

### Post by RavanH on 2007-07-24
Same problem here...  :( 

Brasero log says
```
Session starting:
	flags			= 8279 
	media type	= 0
	speed		= 4
	track type		= 9
	track format	= 63
	output		= none
Session error : the drive can't be locked (Muziek van uw cd's kopiëren)
```

And same with ```
$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

Anybody any idea?

---

