---
title: "Upgrading, need to backup and record video and audio drivers and settings, need help?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by aaronchall on 2009-11-23
OK, I have 9.4 on my laptop, and I want to upgrade to 9.10 by doing a full reinstall.  I've backed up all non-system important data and files.  Video was pretty easy, I recall it was a simple matter to install the Nvidia drivers, but sound was a beast to set up right.  I've finally got the volume buttons actually controlling both the speakers and the woofer simultaneously, and the mute button is finally working.  

Where are the audio drivers and settings stored, so that I know that I know that I know I'll be able to reconfig the audio without too many problems?  If there's already a guide set up, it's OK to just point me to it.

Thanks

Aaron

---

### Post by 3rdalbum on 2009-11-23
I don't know what you had to adjust, so I don't know the file locations would be.

You may find that Ubuntu 9.10 manages your sound correctly.

---

### Post by aaronchall on 2009-11-23
> **3rdalbum said:**
> I don't know what you had to adjust, so I don't know the file locations would be.
 
You may find that Ubuntu 9.10 manages your sound correctly.
 
I hope it does, where would I begin looking for my sound settings and things of this nature?
 
I'm going to try to be more descriptive:
 
Hardware: Inspiron 9300, Nvidia video
 
Installed: PulseAudio Device Chooser, PulseAudio Manager, PulseAudio Volume Control
 
Apparent settings from GUI: 
[LIST]
[*]Volume Control: Device: Intel ICH6 (Also mixer); Under playback tab: Master @ 50%, Master Mono muted, others 100%; under preferences, all selected down to IEC958 Playback AC97-SPSA, PC Speaker on down not selected
[*]PulseAudio Volume Control: Playback tab: mono 100%, ALSA plugin[firefox-3.5]: ALSA Playback 100%; Output Devices: Simultaneous output to Intel ICH6 100% both, Intel ICH6 - Intel ICH6 60% both
[*]Sound Preferences:  all autodetect except audio conferencing: sound capture  USB headphone set USB audio (ALSA) (not connected), Default Mixer Tracks, Device Capture: Intel ACH6 (PulseAudio Mixer)
[*]Hardware Drivers: Nvidia accelerated graphics drivers 96, 173 dormant, 180 active.
[/LIST]And now that I'm looking at it, I'm not using the bass, because that's controlled by the master mono, and it's muted, so I never did get them synchronized for control with the media buttons.  Maybe 9.10 will have a solution?  Maybe I should just boot with a live-cd and see what happens?
 
I managed to save my whole command line history into tomboy notes, so I guess I just need to move forward instead of suffering from paralysis by analysis.
 
Aaron

---

### Post by Buuntu on 2009-11-23
Download the .ISO of Ubuntu 9.10 here -> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and burn it to a disc.
Boot up from the disc and try it "Without any changes to your computer".  When you reach the desktop manager, just play some music or anything that makes sound.
This will let you know if you even have to deal with all the problems you had for your audio on 9.04.  It makes sense to test if it will even not work first though.

---

