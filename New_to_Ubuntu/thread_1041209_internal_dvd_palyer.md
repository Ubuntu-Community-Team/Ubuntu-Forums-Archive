---
title: "internal dvd palyer"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by DarinB on 2009-01-16
How can i find out if my internal dvd player will play a dvd+r with out actually buy one and trying it. 
reason:::: i need to convert vhs to dvd and the one way seems to buy a dvdrecorder/vcr and converting them that way. but some are dvd+r and some are dvd-r the less expensive ones are +r

---

### Post by bekind2thenoob on 2009-01-16
DvD+R drives/recorders should be able to play the DvD-R as well as +R

---

### Post by DarinB on 2009-01-16
sorry about my typo...
is there a device manager type list that i can id the type of dvd player i have installed????

---

### Post by mc4man on 2009-01-16
> is there a device manager type list that i can id the type of dvd player i have installed???? 

In a terminal
```
sudo lshw -C disk
```

---

### Post by DarinB on 2009-01-16
hmmm didn't give any product info, anything in gui???

---

### Post by Yashiro on 2009-01-16
If that doesn't return info you either typed it incorrectly or something is badly broken.

Applications menu, Accessories, Terminal, enter
*sudo lshw -C disk*

```
$ sudo lshw -C disk
[sudo]
  *-cdrom                 
       description: DVD writer
       product: DVD-RW  DVR-106D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.07
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

```

You should get something like that.

---

### Post by BDNiner on 2009-01-16
It should be writen on the front of dvd drive.

---

### Post by mc4man on 2009-01-16
Almost all dvd drives will at this point playback dvd+r media.
What you would be looking for from the lshw was the model and the firmware, you can do a quick google to ck. compatability.

Using the previous post as ex, red is firmware

> -cdrom                 
       description: DVD writer
       product: DVD-RW  DVR-106D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: [COLOR="Red"]1.07[/COLOR]
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

Note that lshw never shows dvd+r even when drive is capable.

Your only real issue would be to make sure you 'finalize' the dvd in your standalone recorder or it won't play on pc dvd drive

---

### Post by DarinB on 2009-01-16
thank you for the info i was wondering because this dvd player is from 2002.

---

### Post by DarinB on 2009-01-16
BTW this is the terminal results
 *-cdrom:0
       description: DVD reader
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio dvd
       configuration: status=nodisc

and the info from the original pc invoice
DIGITAL VIDEO DISK DRIVE..., 680M, 16X, I, 5.25" FORM FACTOR..., LITEON..., CHASSIS 2001..., V3
 So should i buy a dvd -r or +r

---

### Post by Son of William on 2009-01-16
The 680M appears to be a DVD-ROM drive made for installation with Dell computers.  It will read a DVD but it will not write to one.

You probably have to buy a new drive if you want to burn DVD discs.:(

---

### Post by mc4man on 2009-01-16
That's pretty old, looks like a dell 4500. Unfortunately can't find any specs on the drive itself.

dvd-r will definitely work, as far as dvd+r you'd have to try one or keep searching.  
The problem is while liteon made the drive it probably has dell's firmware V3 (or whoever made the pc if not dell.
That makes it hard to track down

---

### Post by DarinB on 2009-01-17
thank you mc4man your response is clear and the most on target. 
Did the old players not play dvd+r and only Play dvd-r???
i wonder how much a dvd+- rw r would cost??
may be worth getting? i suppose i could replace my cdrw with it and still be able to burn cd? **is that correct that dvd rw r's also burn cd r and rw's?????????????**

---

### Post by mc4man on 2009-01-17
> is that correct that dvd rw r's also burn cd r and rw's?????????????
Most definitely, in many cases they burn and read cd's better than a cdrw drive.
I actually used to have the same cdrw you have, long gone now.
Prices are very reasonable, figure $40-80 for a good quality drive
> 
Did the old players not play dvd+r and only Play dvd-r???
dvd-r was the orig., dvd+r came out shortly after, it was more an issue with standalone dvd players, many couldn't playback burned dvd+r's. Not an issue anymore.

Small note - don't buy cheap store label blank dvd media, stick to a name brand
Always a lot of useful info here, and in it's forum

[http://www.cdfreaks.com/](http://www.cdfreaks.com/)

---

