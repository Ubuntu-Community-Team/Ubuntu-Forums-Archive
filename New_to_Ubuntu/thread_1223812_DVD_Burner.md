---
title: "DVD Burner"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-07-26
Hi

Can someone recommend a good DVD burner please

---

### Post by halitech on 2009-07-26
I've got an LG GH22NS30 (sata) that has been going strong for me, burns cd, dvd+/-, dvd dl and dvd rw.

---

### Post by Anybloodyid on 2009-07-26
Hi

May have made a mistake here, I mean which software program can I use.

---

### Post by SunnyRabbiera on 2009-07-26
> **Anybloodyid said:**
> Hi

May have made a mistake here, I mean which software program can I use.

Well what kind of DVD are you aiming for, data DVD or movie DVD?
Ubuntu already has a DVD burining tool built in called brasero, but its mainly for data DVD's.
For movies I would vote DeVeDe

---

### Post by halitech on 2009-07-26
some like Brasero, personally I use K3B even though I use XFCE and not KDE

---

### Post by RedSingularity on 2009-07-26
I use brasero all the time.  Works great!

---

### Post by halitech on 2009-07-26
> **SunnyRabbiera said:**
> Well what kind of DVD are you aiming for, data DVD or movie DVD?
Ubuntu already has a DVD burining tool built in called brasero, but its mainly for data DVD's.
For movies I would vote DeVeDe

Devede doesn't burn natively, it tosses it at K3B (least in my case) to do the actual burning

---

### Post by Ji Ruo on 2009-07-26
k3b works great for data or image files. k9 is apparently the best if you're backing up your movies.

---

### Post by SunnyRabbiera on 2009-07-26
> **halitech said:**
> Devede doesn't burn natively, it tosses it at K3B (least in my case) to do the actual burning

Yeh I know, but DeVeDe does a pretty good job at making the iso for the video disk.
so far its the best movie DVD software I have encountered, I used to use nero and DeVeDe is pretty cool on its own.

---

### Post by Anybloodyid on 2009-07-26
Thanks Everyone

I'm burning Movies I tried Brassero but it didn't work.
I get this pop up
> 
Please replace the disc with a supported CD or DVD
It is not possible to write with the current set of plugins

The disc I'm using is DVD + R DL

---

### Post by halitech on 2009-07-26
> **SunnyRabbiera said:**
> Yeh I know, but DeVeDe does a pretty good job at making the iso for the video disk.
so far its the best movie DVD software I have encountered, I used to use nero and DeVeDe is pretty cool on its own.

I agree, and using it to create an ISO makes it easy for k3b to burn as an image

> **Anybloodyid said:**
> Thanks Everyone

I'm burning Movies I tried Brassero but it didn't work.
I get this pop up


The disc I'm using is DVD + R DL

unless you have a player that supports avi/divx/etc you need to create the dvd menus etc to have a playab;e dvd. Use Devede, easy to use and works great.

---

### Post by Anybloodyid on 2009-07-27
OK Devede made an iso image now how do I burn the image to disc?

Brasero is still reading the same error.

Is there a better program for burning DVD's?

---

### Post by halitech on 2009-07-27
use k3b to burn the image

---

### Post by Anybloodyid on 2009-07-27
Thanks Halitech

But still no luck, I guess Brasero and K3b can not yet read DVD-R DL disc

---

### Post by halitech on 2009-07-27
I've used K3b to burn DL disks with no issues. what does it give for a message on why it won't burn?

---

### Post by LookTJ on 2009-07-27
> **Anybloodyid said:**
> But still no luck, I guess Brasero and K3b can not yet read DVD-R DL discWhat brand of DVDs do you have?

:)

---

### Post by Anybloodyid on 2009-07-27
Closed it opened it again and it seems to be working, will let you know later if success or not.

---

### Post by wizard10000 on 2009-07-27
> **SunnyRabbiera said:**
> Yeh I know, but DeVeDe does a pretty good job at making the iso for the video disk.

I use DeVeDe also and like it but creating an iso is just an extra step for both DeVeDe and your burning program.  If you just have DeVeDe create the DVD structure you can use your burning program to burn VIDEO_TS and AUDIO_TS to a data DVD and you'll have exactly the same thing without taking the time, disk space and CPU cycles create an iso - and your burning program won't need to break the iso down to make the DVD.

A side note - at least for me, brasero has sucked mightily.  I've been using gnomebaker because it doesn't seem to have the same issues brasero does.

Strange, though - all of them are just a frontend for command-line applications.

---

### Post by Anybloodyid on 2009-07-27
Thanks everybody

It all worked.  :D

I had an avi movie which i changed to an iso with Devede
then burned it to disk using K3B

---

