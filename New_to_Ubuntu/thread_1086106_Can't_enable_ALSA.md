---
title: "Can't enable ALSA"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-03-03
Running 8.10 32-bit. 

Setup Information:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

```ALSA version 1.0.17
System is completely updated, but is running kernel 2.6.27-7-generic instead of  2.6.27-11-generic. The newer kernel is completely corrupted on my system.

TV audio out---->--->-->-->
mp3------>------>----->--->  HTPC
Computer Speakers<--<----<--
TV Speakers<----<----<----<-
I hope that diagram makes clear my situation. I have my TV output it's audio to the "audio in" port on my soundcard. This is so if I am watching a TV program or playing my PS3 I can output to my speakers. I have a spare male-to-male headphone cable that a guest could use to hook up an ipod/iphone/etc attached to the microphone input. 

The Problem:
I had Ubuntu (AMD64) running and the audio worked fine. I changed the sound preferences to use ALSA for all device options. Then, I could change the channel volume in alsamixer to get in input channels working. I could also make the volume very loud by maxing several channels. I need this because I have quite a bit of interference if I turn the volume on the speakers up too much. 

Now that I've reinstalled, I can't seem to get ALSA to enable. I changed the settings in System--->Preferences--->Sound from Pulsaudio, but the only channel available in alsamixer is the master pulseaduio one. I've restarted several times too. 

I really want to get ALSA working because I can't seem get the volume loud enough and unmute input channels. 

Thanks for the help

---

### Post by jbrown96 on 2009-03-04
Found a guide for it [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/")

---

