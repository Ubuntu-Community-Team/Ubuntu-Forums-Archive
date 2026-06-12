---
title: "Having problem with USB Headset"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by ovroniil on 2009-09-25
I have just installed Ubuntu 9.04 on Dell Inspiron 6400. I connected a USB headset [model HS-4075p] but Dell couldn't detect that completely. That headset has a volume controller to control the volume of laptop. That controller worked well (with that controller I can control my Laptop's speaker volume!) but the ear-phone and microphone didnot work.

Here is the output of "aplay -l"

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
How to make that work? Any suggession?

---

### Post by ovroniil on 2009-09-28
**Bump**

---

### Post by hellmet on 2009-09-28
Did you try changing the device in Volume Control? Also try installing PulseAudio Audio Switcher or something like that. With that you can change your audio output device live. I used it long time back when I had a USB headset from Philips.

---

### Post by ovroniil on 2009-09-28
> **hellmet said:**
> Did you try changing the device in Volume Control? Also try installing PulseAudio Audio Switcher or something like that. With that you can change your audio output device live. I used it long time back when I had a USB headset from Philips.

Yeap... I've tried from Volume Control! But nothing happend.
Where can I find " PulseAudio Audio Switcher"? It is not in Synaptic.

---

### Post by ovroniil on 2009-12-09
I've installed Karmic now and the same problem exists. Karmic found my headset but the headset does not work with it, except the volume controller. I can only control the PC volume with volume controller of the headset.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any idea to make it work??

---

### Post by Ghost|BTFH on 2009-12-09
If PulseAudio works for you, then you should have to do nothing more than to click on your speaker icon in the upper right hand corner of your screen, open the program and swap out from your sound card to your USB headset by clicking on the appropriate hardware description and you should hear sound from your headset after you adjust the volume controls properly.

Cheers,
Ghost

---

### Post by ovroniil on 2009-12-09
Cool! it works!! 

Just went to sound preferences and selected the audio adapter as a output device.

Thanks a lot!!

---

### Post by Ghost|BTFH on 2009-12-09
Welcome! Glad I could help.  I really have found PulseAudio's concept fantastic, I just wish they would get it to work well without needing a shovel and a sledgehammer.

Cheers,
Ghost

---

