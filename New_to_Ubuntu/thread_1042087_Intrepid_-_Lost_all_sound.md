---
title: "Intrepid - Lost all sound"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Tony Flury on 2009-01-17
my Intrepid installation was working ok - had the nice start up and shut down sounds - the sound test works etc.

After a reboot i have no sound. apart from the error beeps - at least i guess this proves that the speakers are working.

---

### Post by mamamia88 on 2009-01-17
whenever this happens to me i go to a terminal and type

killall pulseaudio

and then i go to system>preferences>sound and change everything to alsa and it works

---

### Post by linux_tech on 2009-01-17
If you havn't already installed these under Intrepid, installing these next they will probably improve  your sound
```

sudo apt-get install alsa-oss
sudo apt-get install gnome-alsamixer
sudo apt-get install libasound2
sudo apt-get install libasound2-plugins

```

open gnome-alsamixer
```
gnome-alsamixer

```
check all settings, make sure nothing is muted

then go to System->Preferences->Sound ..In Devices you will see sound playback- test using both autodetect and alsa 

then test web audio

---

### Post by Tony Flury on 2009-01-17
mamamia88 : I de-installed pulse-audio many days ago, and my sounds worked fine after that.

linux-tech : I have all those packages installed, at the latest version - I checked that by trying to re-install.

nothing is musted - but for some reason it now all works - how odd.

---

### Post by linux_tech on 2009-01-17
Pls check post output of ```
aplay -l
```
and
```
cat /proc/asound/card0/codec#* | grep Codec 
```

---

