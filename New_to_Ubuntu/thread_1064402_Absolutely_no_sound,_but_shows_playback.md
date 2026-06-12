---
title: "Absolutely no sound, but shows playback"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by lkp5002 on 2009-02-08
I know, I know, yet another sound problem thread. I tried the guides, but I think my problem might be entirely different from the usual issues. My problem, I suspect, might be coming from my USB speakers. I'm on a PC, and my monitor doesn't have built in speakers so I can't check if the sound works without the USB speakers. I know that my sound card works, and I know that the speakers work because just a week ago when I was running Windows XP they were just fine. I have tried messing with the sound preferences in ALSA mixer but no combination gave me sound. 

Think something went astray with Ubuntu:

> **** List of PLAYBACK Hardware Devices ****
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Any ideas would be great, because I have no clue how to fix this!

---

### Post by kansasnoob on 2009-02-08
I'm not sure but I have USB speakers and got them working through gnome-alsamixer which is in synaptic or can be installed from terminal:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video:

[ATTACH]102702[/ATTACH]

[ATTACH]102703[/ATTACH]

Compare and see if you can get things working that way. If not I'd follow the appropriate steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by lkp5002 on 2009-02-08
I tried  both of your suggestions, kansasnoob, but I still have no sound.

---

### Post by Guille Damke on 2009-02-08
Try checking all the boxes in alsa-mixer (shown when click "preferences" in the volume control). Then play with these volumes.

---

### Post by lkp5002 on 2009-02-08
Still nothing. Neither the speakers nor headphones work--there's absolutely no sound. Can't hear music, video, or even the start up sound (not sure what it is, but I assume there's some sound when you start up based on other sound problem posts).

Should the USB speakers be listed as a card in aplay -l? (see OP for the aplay -l output)

---

