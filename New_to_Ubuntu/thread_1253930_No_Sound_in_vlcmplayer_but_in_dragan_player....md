---
title: "No Sound in vlc/mplayer but in dragan player..."
date: 2009-08-30
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-08-30
Running Kubuntu 9.04 32bit and I'm having problems with video sound on any mplayer and on the  mplayer frontends I have installed as well as vlc but I get sound in dragon player:confused:

Please help

---

### Post by kamitsukai on 2009-08-30
> **kamitsukai said:**
> Running Kubuntu 9.04 32bit and I'm having problems with video sound on any mplayer and on the  mplayer frontends I have installed as well as vlc but I get sound in dragon player:confused:

Please help


Scrap that somehow PCM got muted:confused::confused::confused:

---

### Post by Ric_NYC on 2009-08-30
Try this... See if it works.

Open VLC.

Tools>Preferences>Audio>Output (then select a different output... Like Alsa etc). Save and play something to test it.

---

### Post by kfox112 on 2010-06-22
Just in case this will help someone else:

After installing VLC media player on Kubuntu 10.04, I had no sound.  I have an HP DV3 laptop.  To fix my problem, I had to go to Tools>Preferences and select all under "Show Settings" at the bottom left.  I expanded the audio menu on the left, and then expanded "Output Modules".  Note that you CAN expand output modules.  I don't just mean select output modules.  ;)

Under the expanded output modules, another menu appears for "Alsa".  On the Alsa tab, I had to refresh the list of possible devices and select my audio device.  Lastly, I had to click on "Output Modules", which is the parent menu to "Alsa", and select Alsa Audio Output. 

Hope that helps someone else.

---

