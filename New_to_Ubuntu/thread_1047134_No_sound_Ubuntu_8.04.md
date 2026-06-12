---
title: "No sound Ubuntu 8.04"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by di5may on 2009-01-22
Hello, i am a complete beginner and have a problem with the sound.. the weird thing about it is that i can hear the drums when logging in at the splash screen... but then nothing seems to playback sound while using the system..

I installed all alsa drivers, library, firmware and utilities... but still get this message when i got to system->preferences->sound:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

Thnx in advance

---

### Post by Michael.Godawski on 2009-01-22
hi,

have a look here:


[LIST]
[*][https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[/LIST]
Also try this in terminal:

```
sudo /etc/init.d/alsa-utils restart
sudo chmod 666 /dev/snd/*
```and also this.
```
rm ~/.asoundrc*
```solutions suggestions taken from:
[https://answers.launchpad.net/ubuntu/+question/5455](https://answers.launchpad.net/ubuntu/+question/5455)

Just copy and paste the commands into the terminal to be sure you don't miss anything.

---

### Post by di5may on 2009-01-22
Thanx! it worked:)
cheers

---

### Post by Michael.Godawski on 2009-01-22
Goot to hear. :)

Then please mark as solved.

---

