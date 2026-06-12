---
title: "hdd conundrum"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by nnjond on 2010-09-17
hdd conundrum

Hi,

I hope i can clarify my situation: My prefered hard drive is the more recent type, SATA I believe. This vibrated on the 1st 2 occasions i booted up after the mobo respnded with 2 beeps on each time. But a black scrn message said something to the effect of it didnt recognise my os or it couldn't mount my drive. After i had fiddled about with it a bit, there was no longer a beep on the third boot, and neither of two 'SATA drives' would vibrate although I can acces them with another pc.

When I substitute them for the older type hdd, 'IDE' i beleive, Their is still no beep, but it goes ahead and loads the Ubuntu 10.04 Lynx os normally.

Can you asist me in establishing my preferred SATA hdd?

Thanks for your time.

(This was my 1st post):
my new pc passed the peep twice and i could feel the my pre-existing hdd vibrating, but a black scrn message said something to the effect of it didnt recognise my os, lynx. On the 3rd boot up, it didn't beep and my hdd didn't vibrate.

I sbstituted my hdd and booted up; it still didnt peep, but went ahead and loaded the lynx os from the different drive.

My pre-existing hdd with all my stuff on it can be accessed. with a usb thingy on another pc?

Can you asist me in establishing my pre-existing hdd?

Thanks for your time.

---

### Post by MooPi on 2010-09-17
Have you installed anything to the offending hard drive or is it empty/bare ?

---

### Post by nnjond on 2010-09-17
The hardrive in question has 10.04 on it and was working perfectly. I can still access it and my home dir by attaching it to another pc

---

### Post by cariboo on 2010-09-17
Does the sata drive show up in the BIOS when connected?

---

### Post by nnjond on 2010-09-17
The drive is on SATA 1. BIOS shows SATA 1-4 undetected, along with slave IDE, while my dvd is connected as Primary Master.

When  I substitute My SATA drive for an older IDE hd, it goes ahead and loads the os but the dvd drive no longer shows up in the bios or in the os

---

### Post by MooPi on 2010-09-18
This is giving telltale signs of hardware failure of some nature. It may be your sata controler chip on the motherboard.  It may only be the connection. You may want to try to use a different connector on the motherboard.

---

### Post by nnjond on 2010-09-18
Thanks for your help.

Here's an update; I'm almost back to sq 1!

I've got back my old post beep. However at boot, my display runs:

Verifying pool Data....
Boot from CD
Disk Boot Failure, Insert system disc and press enter.


I can load my os from a live CD but it doesn't show my Hdd.

My BIOS/CMOS reveals;

IDE CHANNEL 0 MASTER: NONE
IDE CHANNEL 0 SLAVE: NONE
IDE CHANNEL 1 MASTER: NONE
IDE CHANNEL 1 SLAVE: DVD/CD
IDE CHANNEL 2 MASTER NONE
"	"	" NONE	

NB: my SATA is using an IDE adapter on the mobo

I can view my oses and home dir data by attaching my hdd to a 2nd pc with a usb addapter and auxillary psu

My spec are

Winfast 760GXK8MC Series 54W1P23 100805
AMD Sempron (tm) 2800+
1gb ram

Thanks for your time.

---

### Post by cascade9 on 2010-09-18
So its the same computer you were having issues booting? 

[http://ubuntuforums.org/showthread.php?t=1575833](http://ubuntuforums.org/showthread.php?t=1575833)

Nice for you to update that thread :P 

I'd try removing the DVD drive, hook the IDE drive and SATA drives up and see if it boots then. I'd use ACHI, not IDE mode. BTW- "my SATA is using an IDE adapter on the mobo"- not quite right. You would be using IDE mode, not ACHI, but that is not an 'IDE adapter'.

---

### Post by Paqman on 2010-09-18
By the way, if you're using conventional spinning hard drives there's no penalty to using IDE instead of SATA, so don't sweat about it too much in the meantime.

---

