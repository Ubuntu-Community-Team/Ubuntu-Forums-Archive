---
title: "I need some help with guitar audio settings"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Li18nxBoy on 2009-05-25
I can seem to get any of the programs on my system to recognize my guitar input.  The sound goes threw my system but I am not able to do anything with it.

Ubuntu 9.04
kernal 2.6.28-12-generic

on-board soundcard
        Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Device 7246

I have tried playing with the settings under sys/pref/sound, using the pulseaudio devise chooser, playing with group permissions, reinstalling all the programs related to what im doing and about 30 or so how-to.


If you need any outputs just ask.

---

### Post by ellgor on 2009-05-26
Hi,

Its not clear what you are trying to do with your guitar, I will assume you are trying to record the input of an accoustic guitar.

I use "Ardour" as the capture programme (pretty impressive it is too) I then open a terminal and type in:

alsamixer   enter it

I note that you mention Pulseaudio, as I use 8.04 I'm not to sure if alsa remains the main audio-contoller, if it is not, go to the multi-media/video section of the forum and follow the sticky there on audio setup, hope this is of help.

Regards, Ellgor.

---

### Post by Li18nxBoy on 2009-06-03
Sorry it took so long to get back on this.

I tried the sticky in the media/video forum but i couldnt get it working...

Its a pipeline problem im sure, when I go into my pulse audio applet and open all my source/sinks volume meters the sound from my media player shows up on hda intel - alc888 analog but i can find the input devise, even tho its being amped threw my sound card.

---

### Post by Li18nxBoy on 2009-06-03
*bump

---

### Post by whitethorn on 2009-06-03
Have you tried right clicking on the volume meter and choosing open volume control, then try around with a couple devices and try unmuting a couple stuff, maybe you'll get some sound.

---

### Post by Li18nxBoy on 2009-06-03
> **whitethorn said:**
> Have you tried right clicking on the volume meter and choosing open volume control, then try around with a couple devices and try unmuting a couple stuff, maybe you'll get some sound.

Yes I have, everything in the volume control applet is working as it should, including the input volume control

---

### Post by Li18nxBoy on 2009-06-04
*bump

---

### Post by ibuclaw on 2009-06-04
Have you tried using JACK Control to start and connect audio services/applications?

---

### Post by Li18nxBoy on 2009-06-04
> **tinivole said:**
> Have you tried using JACK Control to start and connect audio services/applications?

Yes but jack is unable to recognize the input signal.

I have tried playing with the connections inside jack with creox running but all I end up with is distorted feedback/static

---

### Post by ibuclaw on 2009-06-04
> **Li18nxBoy said:**
> Yes but jack is unable to recognize the input signal.

I have tried playing with the connections inside jack with creox running but all I end up with is distorted feedback/static

hmm... never used Creox myself, although you can setup audio connections between applications in JACK by clicking "Connect" in the panel.

Patchage, or so I hear, is another good application for doing this too.

Regards
Iain

---

### Post by Li18nxBoy on 2009-06-04
same thing with Patchage as with the connection manager in the main jack interface

---

### Post by Li18nxBoy on 2009-06-05
*bump

---

### Post by Li18nxBoy on 2009-06-07
*bump

---

### Post by ayenack on 2009-06-07
May seem like a stupid question.... but have you gone to System/Prefernces/Sound and tried changing Sound capture and then testing it with each setting? Give it a go it might work.

Also might be worth giving Audacity a try it's in the repo's.

---

### Post by Li18nxBoy on 2009-06-08
That was the first thing I did, good suggestion tho

I have tried  Audacity also... no luck

---

### Post by Li18nxBoy on 2009-06-08
*bump

---

### Post by Li18nxBoy on 2009-06-09
*bump

---

### Post by Li18nxBoy on 2009-06-10
*bump

---

### Post by 4Orbs on 2009-06-10
If you have the aux input capture and line in capture switches on, and can hear your sounds in the system, Audacity should pick it up. In Audacity you need to click a button beneath the vu graph before it will show any sound on the graph (or maybe you just click on the vu meter).

---

