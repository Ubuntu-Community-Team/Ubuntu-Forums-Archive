---
title: "Built in Mic Not Working -- Acer 7740-5618 Laptop"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by vbartolotta on 2010-09-23
Good Day,

I have Karmic installed on an Acer Aspire 7740-5618 laptop. The built in  microphone doesn't work with any application. I've tried the remedies  in this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) to no avail.

Oddly enough, the microphone works fine when I boot the laptop in Windows 7.

Selecting default devices, adjusting volume levels with the PulseAudio  Volume control doesn't change anything. Alsamixer reports my gains are  set to maximum.

Playback is not a problem. Speaker output is just fine.

Any help is greatly appreciated.

Victor

---

### Post by okplayer02 on 2010-09-24
did you bother to take a look rather the mic is muted 

when you are in the pulseaudio preferences go to the input tab and make sure its not muted.

---

### Post by vbartolotta on 2010-09-25
OKPlayer02,[INDENT]
> **okplayer02 said:**
> did you bother to take a look rather the mic is muted 

when you are in the pulseaudio preferences go to the input tab and make sure its not muted.
[/INDENT]I don't think I have the mic muted. Which preferences tab are you referring to? There is a PulseAudio volume control, a device chooser, two volume meters, configure local sound server, preferences and more. 

Victor

---

### Post by BigRedButton on 2010-09-29
I have the same problem with an acer d250 netbook. no, it isn't muted. under multimedia systems selector in the inputs section pulseaudio lists "default" and two unknowns. looking at the pipelines listed one of the unknowns is the sound card output, and one is input. when I test them, the output works fine (the normal tone) but when I test the input, it feeds back (which makes no sense, so I know it's a software deal). but even when I leave it there I get nothing from "Sound Preferences" or any program (except sound recorder, which for some reason works under absolutely any circumstances on any hardware)

---

### Post by BigRedButton on 2010-09-29
fixed [http://ubuntuforums.org/showthread.php?t=1486087&highlight=built+microphone+mic]("http://ubuntuforums.org/showthread.php?t=1486087&highlight=built+microphone+mic")

I also had to install gnome-alsamixer in synaptic, the mic didn't start responding until I brought it up and moved the capture gain slider. not sure why... but heck now it works so I'm not going to complain.

---

### Post by vbartolotta on 2010-09-30
I installed the gnome-alsamixer but it didn't change anything for me. The mic is still dead. Works fine when I boot in Windows 7.

Victor

---

### Post by jbweimar on 2010-10-09
I have the same problem. I'm running Ubuntu 10.4 on a Toshiba Satellite T235 with Intel G45 DEVIBX / REALTEK ALC259. All the volume controls are up. Nothing is muted. Mic works fine when I boot up in Windows 7. I can play music. It's just the microphone that does not register anything. I even updated to the latest 10.0.23 version of ALSA but still without success. I think I am going to try to install OSS... but what a hassle!

---

