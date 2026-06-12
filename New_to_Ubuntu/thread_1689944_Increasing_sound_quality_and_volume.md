---
title: "Increasing sound quality and volume"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by kaxenti on 2011-02-17
**[Solved]**
I said to myself: "This is the last one I'll try, then I'll just put it  back before I break it" and wham! After putting up with this volume for  so long, can't believe I finally fixed it.

I wasn't even sure this was having any effect but I was trying out  different HD Audio models from  /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz and into  /etc/modprobe.d/alsa-base.conf and eventually, found one that has  tremendously boosted the volume and the quality no longer deteriorates.  Maybe the solution was obvious but I didn't have a clue how to know  which model to pick and since going from one model to another wasn't  having any noticeable effect, it was hard to know whether I should  bother keeping on trying.

In case anyone wants to know, my motherboard is ASRock ConRoeXFire-eSATA2 and the model that worked was targa-8ch-dig. 

Thanks again for attempting to help, appreciated! :)
(P.s. Is it just me or do the smiley faces look as though they are up to no good?)
**[Solved]**
============================================================
Hi all,

It's been a while since I played with all my sound settings and drivers and I know it's a lot to ask but I was wondering if there was any way that I could increase the sound quality and volume. I've had this install for quite a while now and the sound is acceptable but within my XP install, I could get the volume about 6-8 times higher (deafening at that point but having it a few times higher would be nice). The quality also distorts (static) a little bit when the volume is maxed (on ubuntu). Let me just point out, I'm more concerned with increasing the maximum volume level than fixing the sound quality (as it's mostly acceptable).

I'm not sure what details would be required but I've attached a screenie of alsamixer (a few things missing further on the right but they are just mic settings).
There is also a lot of sound and other hardware [COLOR=Blue][info here]("http://www.alsa-project.org/db/?f=52e83806a12030a578af1a676a2b007161e6ae3f")[/COLOR] (from an alsa project script).
If you require any other info, just ask!

I'm running Lucid Lynx and I doubt it makes any difference but I only ever use headphones. 

Thank you for your time and any help!

---

### Post by sydbat on 2011-02-17
> **kaxenti said:**
> Hi all,

It's been a while since I played with all my sound settings and drivers and I know it's a lot to ask but I was wondering if there was any way that I could increase the sound quality and volume. I've had this install for quite a while now and the sound is acceptable but within my XP install, I could get the volume about 6-8 times higher (deafening at that point but having it a few times higher would be nice). The quality also distorts (static) a little bit when the volume is maxed (on ubuntu). Let me just point out, I'm more concerned with increasing the maximum volume level than fixing the sound quality (as it's mostly acceptable).

I'm not sure what details would be required but I've attached a screenie of alsamixer (a few things missing further on the right but they are just mic settings).
There is also a lot of sound and other hardware [COLOR=Blue][info here]("http://www.alsa-project.org/db/?f=52e83806a12030a578af1a676a2b007161e6ae3f")[/COLOR] (from an alsa project script).
If you require any other info, just ask!

I'm running Lucid Lynx and I doubt it makes any difference but I only ever use headphones. 

Thank you for your time and any help!A couple of questions...

1) How have you installed Ubuntu? In it's own separate partition? As a WUBI install (as a 'program' inside Windows)? Knowing this *might* make a difference.

2) Have you checked what level your volume control applet is set at? If it is not visible in one of your Panels, you can right click on a panel and choose "Add to Panel", then pick "Indicator Applet" from the list.

---

### Post by kaxenti on 2011-02-17
> **sydbat said:**
> A couple of questions...

1) How have you installed Ubuntu? In its own separate partition? As a WUBI install (as a 'program' inside Windows)? Knowing this *might* make a difference.

Yes, I've installed it in its own partition, it actually has its own physical drive so not within Windows.

> **sydbat said:**
> 
2) Have you checked what level your volume control applet is set at? If it is not visible in one of your Panels, you can right click on a panel and choose "Add to Panel", then pick "Indicator Applet" from the list.
It's set to max, or well, it wasn't but the max level there is the same as the volume control I use (the one also shown in alsamixer) - I can put it above 100% but the sound quality deteriorates drastically making it pointless to do (within Windows, I was able to get it just as high if not higher without loss of quality).

Thank you for the reply

---

### Post by sydbat on 2011-02-17
> **kaxenti said:**
> Yes, I've installed it in its own partition, it actually has its own physical drive so not within Windows.


It's set to max, or well, it wasn't but the max level there is the same as the volume control I use (the one also shown in alsamixer) - I can put it above 100% but the sound quality deteriorates drastically making it pointless to do (within Windows, I was able to get it just as high if not higher without loss of quality).

Thank you for the replyWhat gstreamer codecs do you have installed? I make sure to install all of them (good, bad and ugly). 

I have never had a problem with sound volume, so this is the limit of what I can offer. Sorry.

---

### Post by kaxenti on 2011-02-17
I'm pretty sure I have all the GStreamer codecs installed (from the looks of Synaptic Package Manager, including bad and ugly).

Thank you very much for trying anyway :)

---

