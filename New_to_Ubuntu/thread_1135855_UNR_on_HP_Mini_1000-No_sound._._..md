---
title: "UNR on HP Mini 1000-No sound. . ."
date: 2009-04-24
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-04-24
Hi!  I have an HP Mini 1000 running UNR 9.04, however, I have no sound.  I have tried ALSA, OSS, and PulseAudio, but no avail.  The interface would appear to be detected, but I get no output.  What can I do to remedy this?

Thanks in advance!

---

### Post by cloudburst on 2009-04-24
This may not be any help, but these are the models that either work well with UNR, work well enough or don't function properly with UNR.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by cloudburst on 2009-04-24
> HP Mini 1000

Jaunty UNR works on the HPMini, including wireless. However there is a known bug with audio not working at the moment.

    *

      318942 - no sound from speakers on HP Mini 1000 (hda-intel, IDT 92HD75B2X5) 

From the linked wiki page. I don't think you can solve this problem until updates from the Canonical team are made to solve this problem.

---

### Post by pi.boy.travis on 2009-04-24
> **cloudburst said:**
> This may not be any help, but these are the models that either work well with UNR, work well enough or don't function properly with UNR.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

Thanks.  I didn't know there was a bug report for this.

---

### Post by cloudburst on 2009-04-24
No problem. It will probably be fixed soon. The UNR team is rather good. Sorry I couldn't help.

---

### Post by mozillar on 2009-04-25
Hi, I posted a workaround that may help [here]("http://ubuntuforums.org/showthread.php?t=1136225").

---

### Post by pi.boy.travis on 2009-04-25
Fantastic!  Thanks you!

---

### Post by EtherNomad on 2009-05-12
HP Mini 1000 (1030nr) + Jaunty Full 9.04
I installed Jaunty the night it was released and had sound straight out of the box. Updates killed my sound at some point. Here is how I recovered full use of speakers and mic (Skype works like a champ!)
 Enable Sound, Video & Mic (Skype)
- System | Administration | Software Sources
-- Click Updates tab and enable "Pre-released updates (jaunty-proposed)
- System | Preferences | Sound
-- Select "ALSA - Advanced Linux Sound Architechture" for all
- Download and install Linux Kernel 2.6.28.12-generic or above...reboot
- Launch terminal and check kernel version
-- cat /proc/sys/kernel/osrelease
- Type sudo alsamixer and click tab twice to show all
- Adjust settings to match the following:
-- Master = 68 | Headphone = 79 | PCM = 100 | Front = 100 | Capture = 60 (Space Bar to enable) |
-- Capture 1 = Disabled | Analog Loopback = Off | Analog Loopback 1 = Off | DAC0 - Enabled 84 |
-- DAC1 = Disabled | Import0 = Enabled 100 | Import1 = Disabled | Input Source = Line | Input Source1 = Line |
-- Mux = 0 | Mux1 = 0 |
-- Click Escape to exit
- Download and install Skype (use .deb package)
- Launch Skype | Options | Sound Devices
-- Change all 3 to "HDA Intel (hw:Intel,0)
- Video Devices
-- Enable Skype Video
-- Start my video automatically when I am in a call
 I am doing this with alsa v.1.0.18.
Some people might gripe about the 2.6.28.12-generic kernel but let me say, every utility and application I've tested works perfectly! Note that some of the settings in alsamixer are arbitrary but what I've posted above works 100% for me.

---

