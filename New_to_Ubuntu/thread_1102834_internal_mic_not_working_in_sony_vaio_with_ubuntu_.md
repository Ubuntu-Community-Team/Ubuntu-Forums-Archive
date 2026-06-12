---
title: "internal mic not working in sony vaio with ubuntu 8.04"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by hmo on 2009-03-22
I have a sony vaio with ubuntu 8.04 (x64) the vaio model is VGN-SZ770FN
I cannot use skype because the internal mic is not working. Following [some suggestions I did this]("http://www.land-of-kain.de/docs/sony_vaio_sz61_mnb/"):

nano -w /etc/modprobe.d/alsa-base
    alias snd-card-0 snd-hda-intel
    options snd-card-0 index=0
    options snd-hda-intel model=vaio

But it doesn't work. 
Also I realized that I have no option for internal mic , if I check in Volume control, Edit -> Preferences I have:
Master
PCM
Digital

Any clue about a way to fix this?

---

### Post by arochester on 2009-03-22
Have you look at "Comprehensive Sound Problem Solutions Guide" on [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by mlichtenstein2 on 2010-04-17
I did not get my internal mike working also. Therefore I bought a cheap external mike and did the following to make it work:
System->Preferences->Sound

Sound Events
Sound playback: Autodetect

Music and Movies
Sound playback: Alsa- Advanced Linux Sound

Audio Conferencing
Sound playback: Autodetect
Sound Capture: Alsa- Advanced Linux Sound

Test with Applications->Sound & Video->Sound Recorder
Record from input is set to capture.
Set Record as: voice, lossless wav audio

---

### Post by lidex on 2010-04-18
Did you see this thread? Don't miss the last post.
[http://ubuntuforums.org/showthread.php?t=1043352]("http://ubuntuforums.org/showthread.php?t=1043352")

---

