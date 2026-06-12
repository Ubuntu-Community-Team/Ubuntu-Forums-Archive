---
title: "PC Freezes"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by azzaw on 2009-08-19
Hello, I am an absolute beginner.  I am trying to rip a dvd.  Every time I ask one of the DVD ripping programs, Acidrip, k9copy, dvdrip, or mplayer to play a dvd the pc freezes.  The only way I can get enything to happen is to restart the pc.  Thanks for any help in advance.

---

### Post by rajeev1204 on 2009-08-20
> **azzaw said:**
> Hello, I am an absolute beginner.  I am trying to rip a dvd.  Every time I ask one of the DVD ripping programs, Acidrip, k9copy, dvdrip, or mplayer to play a dvd the pc freezes.  The only way I can get enything to happen is to restart the pc.  Thanks for any help in advance.


Well,ripping a dvd is a processor and ram intensive process with a lot of hdd acess,Maybe your system is slow ?

Try stopping all other programs,close all windows then try to rip.

---

### Post by pedro3005 on 2009-08-20
Can you normally play the DVD using VLC?

---

### Post by blur xc on 2009-08-20
> **azzaw said:**
> Hello, I am an absolute beginner.  I am trying to rip a dvd.  Every time I ask one of the DVD ripping programs, Acidrip, k9copy, dvdrip, or mplayer to play a dvd the pc freezes.  The only way I can get enything to happen is to restart the pc.  Thanks for any help in advance.


I've ripped several dvd's using handbrake.  I don't know about those other programs, but handbrake is written to utilize multi core processors.

My machine is a core  2 duo 3ghz, w/ 4 gigs ram (32 bit though, so only 3.2gig usable) and ripping  a dvd runs both cores of my processor at 80 - 90%  capacity, for a solid 20min.

Handbrake is nice because it has some fancy presets for common output formats, ie.- ipod, ipod touch/iphone, psp, etc...  It takes some of the mysticism out of all those bit-rates, frame rates, codecs, etc...  If it wasn't for the presets, I wouldn't be able to use it.

BM

---

### Post by Ms_Angel_D on 2009-08-20
My PC freezes as well at any sign of Disk being inserted into the drive, funny thing is, this doesn't happen under windows, only Ubuntu.

I have opened a bug, you can have a look at it to see if this is they same situation and perhaps contribute to let dev's know this affects you as well.

[https://bugs.launchpad.net/ubuntu/+bug/338961](https://bugs.launchpad.net/ubuntu/+bug/338961)

---

### Post by LowSky on 2009-08-20
sounds like a hardware driver issue. Is the drive a SATA or IDE connection?

If IDE is it set to Master Slave or Cable Select?

If SATA, what mode is BIOS set to, Legacy IDE or ADHC, it can be checked from BIOS.

---

### Post by LewRockwell on 2009-08-20
what hardware?

and why are we the first to ask?

{{sigh}}

.

---

### Post by rajeev1204 on 2009-08-21
> **LewRockwell said:**
> what hardware?

and why are we the first to ask?

{{sigh}}

.

I already hinted in my post about the system being slow.So we wait for the reply now i guess.

---

### Post by azzaw on 2009-08-23
Tanks every one for your help.  I had to install **libdvdcss2** and **libdvdread4**.  After this everything is fine.  Thanks all for your help.  I found these under synaptic.  Hope this helps "Ms_Angle_D".

---

