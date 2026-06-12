---
title: "No Sound when on Youtube"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by CSHANKY on 2009-09-14
Can someone help? My Creative sound card works fine...but can't hear a peep on Youtube.

Flash is installed.

File name:  libflashplayer.so
Shockwave Flash 10.0 r32

---

### Post by QIII on 2009-09-15
Check Synaptic to see if swfdec or gnash is installed.  Uninstall them both, since they conflict with Flash.

If they aren't there, then there are other things to look at.

Try uninstalling those two first.

---

### Post by starcannon on 2009-09-15
Make sure some other app isn't holding the sound card hostage. I have to shut down Rhythmbox or Banshee before I can hear other media such as flash.

---

### Post by CSHANKY on 2009-09-15
swfdec or gnash - uninstalled. 

Still NO sound on Youtube. VLC and Creative Audigy Soundcard work fine......

---

### Post by DasEi on 2009-09-15
sudo apt-get install ubuntu-restricted-extras vlc mozplugger

---

### Post by CSHANKY on 2009-09-15
Nopes ! Youtube sound doesn't work.....

---

### Post by QIII on 2009-09-15
I don't have a quick answer for you, then, but take a look here:

[https://bugs.launchpad.net/ubuntu/+bug/367173](https://bugs.launchpad.net/ubuntu/+bug/367173)

---

