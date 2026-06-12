---
title: "static sound at startup"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-05-21
hi,

I am running Ubuntu 9.04 off a Lenovo X200 Tablet. Fresh install yesterday. Everything seems to be running fine, except the sound. 

I can record sound and hear the playback in the sound recorder at Applications --> Sound & Video --> Sound Recorder. However, when Ubuntu starts up, instead of the log-in sound i hear a bunch of static. 

The "Sound" option under System --> Preferences is also glitchy. When I put the driver to "Autodetect" and press test, i get the same static sound i hear at log-in. The only driver that will work is OSS (Open Sound System) but that still gives me static at startup. 

How can I go about to fix this problem?

---

### Post by acreech on 2009-05-21
> **akimatsu123 said:**
> hi,

I am running Ubuntu 9.04 off a Lenovo X200 Tablet. Fresh install yesterday. Everything seems to be running fine, except the sound. 

I can record sound and hear the playback in the sound recorder at Applications --> Sound & Video --> Sound Recorder. However, when Ubuntu starts up, instead of the log-in sound i hear a bunch of static. 

The "Sound" option under System --> Preferences is also glitchy. When I put the driver to "Autodetect" and press test, i get the same static sound i hear at log-in. The only driver that will work is OSS (Open Sound System) but that still gives me static at startup. 

How can I go about to fix this problem?

I have this same problem and it just started on my computer last week. I found a temporary fix. If you left click on the speaker icon in the system tray. Then left click on volume control. Select the Alsa Mixer from the drop down list and make sure that the "Master" and "PCM"  volumes are up. 

This fixed the problem for me. But seems to need reset after a reboot. I am not sure what a permanent fix for this problem is.

---

