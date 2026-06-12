---
title: "Fixing PulseAudio vs. Installing Esound"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by MooseMagnet on 2009-01-03
I went from Feisty to Intrepid today on my Dell laptop. Same configuration details as usual. So far, I like Intrepid.

I had to modify things to get the sound to work correctly.

Rather than follow these instructions:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=usb+mic](http://ubuntuforums.org/showthread.php?t=789578&highlight=usb+mic)

I did this:

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

It seemed easier and quicker, and my sound does now work.

Have you had good results with the pulseaudio fix? I'd like to hear from some of you before I try that more complicated fix.

Thanks.

---

### Post by gettinoriginal on 2009-01-15
> Q. PulseAudio? Bleh! I don't want it on my system.
A. Well... tough! PulseAudio is already installed and active on Hardy and Intrepid by default; it replaces ESD (ESound Daemon) for system sounds, and most of Ubuntu's default applications already use it (Totem, Rhythmbox, and any other applications using the GStreamer framework). Although some high-profile applications support PulseAudio natively (such as VLC and mplayer), most applications use plain ALSA or OSS output, and thus don't have native PulseAudio support.


Hope this helps you decide. :p  The guide you mentioned is great, only takes about 15 minutes, and works perfectly. (At least with my system):p

---

### Post by MooseMagnet on 2009-01-16
Thanks for the feedback. I'm running ALSA. Works fine.

---

### Post by MooseMagnet on 2009-06-27
Well... Back at more hammering on it.

I followed these instructions:
[http://ubuntuforums.org/showthread.p...hlight=usb+mic](http://ubuntuforums.org/showthread.p...hlight=usb+mic)

And all seemed fine and dandy, but Skype would not work. So I did this, and now Skype works.

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

Skype doesn't like pulseaudio? Guess not.

---

### Post by stevoo on 2009-06-27
pulse audio is good ... very good .... if you manage to get it working. 

Managed just once on 7.10 that was it ! never again ! 

I just remove it and install alsa ..... :D

---

### Post by a_flj_ on 2010-01-17
You can only play as many concurrent streams using alsa as many DACs (digital-analog converters) are on your soundcard - most normal, non-pro cards have two. If you watch a movie while listening to some music, two channels are OK. If a system event comes along and plays a notification sound, chances are you need to restart both music and movie to get sound working again, depending on configuration. So you should in all cases install a sound server, be it esd or pulse.

However, pulse has some features that esd has not - one of them is essential for me: it tricks apps which want to talk to alsa directly (most sound servers sit on top of either alsa or oss - both pulse and esd sit on top of alsa in a standard configuration) into believing they talk to alsa when in fact they talk to some fake sound interface created by pulse. Whereas for esd an app needs to be compiled with specific esd support.

I don't know why ppl complain about getting pulse to work. For me, it worked right out of the box on karmic koala. I still need to tweak some apps, but other than that it works.

---

### Post by Ibidem on 2010-07-09
Before you criticize esound too much, read:
man esddsp

esddsp mhwaveedit
works for me.  (I only need that because Ubuntu has disabled esound support there)
I just had xmms (self-compiled), mpg123, ogg123, and mhwaveedit running together, thanks to esd.

I like esound, partly because it doesn't do too much to ALSA stuff, so alsa-based configuration actually works.  Also, it's smaller (~22kb for "esound" deb).

---

