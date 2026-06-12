---
title: "Sound Drivers"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by mary.ydm on 2010-09-13
I have installed Hardy Heron 8.04 on my computer and have a syntax motherboard with on board sound but I can not find the right drivers to make this work can you help?

---

### Post by nothingspecial on 2010-09-13
Hi

Let`s see what your soundcard is

Go to your menu and click Accessories > Terminal

copy and paste this into it

```
aplay -l
```

Then copy and paste the gobbldygook it spits out back here

---

### Post by mastablasta on 2010-09-13
Why did you use the old version of Ubuntu? why not try the latest LTS release Ubuntu 10.04?
 
Also open terminal, copy and paste this command to it (if the one in above post doesn't give anything back):
 
```
lspci -v
```
 
and post the output here.
 
 
here is a good sound troubleshooting thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
 
Drivers are already installed. You just have to make them work. sort of,...

---

### Post by mary.ydm on 2010-09-30
Ok here is what it said:

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



I dont upgrade to 10.4 as I can not get the drivers for my printer and I need my printer to work

---

### Post by mary.ydm on 2010-10-03
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
Subdevices: 4/4
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
Subdevice #2: subdevice #2
Subdevice #3: subdevice #3
card 1: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
Subdevices: 1/1
Subdevice #0: subdevice #0


Is the info I get - how does this help??

---

### Post by cchhrriiss121212 on 2010-10-03
Try typing alsamixer in a terminal, this will show your volume levels. Check these to see if they are loud enough, some cards are muted by default.

---

### Post by mary.ydm on 2010-10-03
Hey have checked my volume levels on the alsamixer in terminal and they seem to be off this is what it says:

&#9474; Card: HDA ATI HDMI                                                           &#9474;
&#9474; Chip: Generic 1002 ATI R6xx HDMI                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: IEC958 [Off]  

So how do I switch on?

---

### Post by cchhrriiss121212 on 2010-10-03
According to your aplay -l output you have two sound devices, the first is an HDMI output (possibly from your video card) and the other is your onboard sound.

I take it you want to use onboard, so press f6 to select this sound device in alsamixer. Then you just move left and right to select channels and up and down to change volume.

You may also want to select this card as default in your preferences>sound menu item.

---

### Post by mary.ydm on 2010-10-12
I tried to press f6 to select this sound device in alsamixer, but this does not seem to work so I cannot just move left and right to select channels and up and down to change volume.

 I have also selected this card as default in my preferences>sound menu item, but it does not stay selected!!!

---

