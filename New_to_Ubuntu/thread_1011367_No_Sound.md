---
title: "No Sound"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Frank_F on 2008-12-14
Hello, I am not able to receive any sound...I currently have 7.10 installed and the sound never worked on feisty as well....sound card is AC97 VT8233/A/8235/8237

Thanks

---

### Post by gettinoriginal on 2008-12-14
Do you have alsa and pulse installed ??

---

### Post by kansasnoob on 2008-12-14
> **Frank_F said:**
> Hello, I am not able to receive any sound...I currently have 7.10 installed and the sound never worked on feisty as well....sound card is AC97 VT8233/A/8235/8237

Thanks

Looks like it may be the same card I have:

> lance@lance-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I always install gnome-alsamixer, it's in synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Look at mine and compare closely to yours:

[ATTACH]96419[/ATTACH]

[ATTACH]96420[/ATTACH]

If you have no luck post the output of:

```
aplay -l
```

That's a lower case L.

---

### Post by kansasnoob on 2008-12-14
> **gettinoriginal said:**
> Do you have alsa and pulse installed ??

7.10 (aka Gutsy) didn't use Pulse audio.

---

### Post by kansasnoob on 2008-12-14
Also this is generally informative:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by sneeks on 2008-12-14
have you un-ticked the digital box in your sound preferences ??

---

### Post by Frank_F on 2008-12-14
dumb question, but where are my sound preferences...I only see System, Preferences, Sound, but dont see any button labeled digital box ?

Thanks

---

### Post by Frank_F on 2008-12-14
This my output...thanks

**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

