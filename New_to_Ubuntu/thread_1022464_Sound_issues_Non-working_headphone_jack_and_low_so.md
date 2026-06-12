---
title: "Sound issues: Non-working headphone jack and low sound volume"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Steve05TSX on 2008-12-26
I still can't figure this out.  I've tried numerous programs to try to increase the volume, but everything is 100%.  It's all the way up on my laptop, all the way up in Ubuntu, all the way up on the headphones.  I'm starting to lose hope.  I did all of the updates hoping this may fix it, still, nothing.  Any ideas?

---

### Post by neu2buntu on 2008-12-26
no expert here,but i will try and help  ...paste the output of ```
aplay -l
```

---

### Post by neu2buntu on 2008-12-26
also some basic stuff, in your volume-control in top panel make sure no outputs are muted(x over speaker) ...just incase

---

### Post by linux_tech on 2008-12-26
If you are familiar with using alsamixer, this command will will show all the alsamixer settings


```
alsamixer -D hw:0
```

you can also use Gnome-alsamixer, but you will need to install it first.


```
sudo apt-get install gnome-alsamixer
```

Then to open gnome-alsamixer type



```
gnome-alsamixer
```

check all settings, make sure nothing is muted;
make sure front, master and headphone is checked


If you havn't already installed these under Intrepid, installing these next they will help improve your sound
```
sudo apt-get install alsa-oss

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```


Also to open volume control type:
```


gnome-volume-control

```

---

### Post by Steve05TSX on 2008-12-26
> **neu2buntu said:**
> no expert here,but i will try and help  ...paste the output of ```
aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Steve05TSX on 2008-12-26
> **neu2buntu said:**
> also some basic stuff, in your volume-control in top panel make sure no outputs are muted(x over speaker) ...just incase

everything is good on that part of it.  I have every sound option I have seen at 100%

---

### Post by Steve05TSX on 2008-12-26
> **linux_tech said:**
> If you are familiar with using alsamixer, this command will will show all the alsamixer settings


```
alsamixer -D hw:0
```

you can also use Gnome-alsamixer, but you will need to install it first.


```
sudo apt-get install gnome-alsamixer
```

Then to open gnome-alsamixer type



```
gnome-alsamixer
```

check all settings, make sure nothing is muted;
make sure front, master and headphone is checked


If you havn't already installed these under Intrepid, installing these next they will help improve your sound
```
sudo apt-get install alsa-oss

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```


Also to open volume control type:
```


gnome-volume-control

```

tried all of these, it actually got my headphone line working by checking the headphone as line out section, but volume is still fairly weak even with everyhting at 100%

---

### Post by Steve05TSX on 2008-12-26
headphones are cranking actually, louder than my external laptop speakers

---

### Post by Steve05TSX on 2008-12-27
still looking for an answer here

---

### Post by 5BallJuggler on 2008-12-27
Just out of interest, are you running an external sound card? 
I had an issue with something similar, I was trying to use an Edirol external, but Ubuntu wanted to use the internal one on my machine, I had to turn that one off in BIOS to get my external working.

Phil

---

### Post by neu2buntu on 2008-12-27
goto >system>preferences>sound and try ALSA -advanced linux sound architecture for the 1st 4 options and HDA intel (alsa mixer) for option 5 ....   there is a test option beside these settings make sure you hear the beep if not try alternate settings

---

### Post by Steve05TSX on 2008-12-27
10 times better when I enabled ALSA, maybe that was the trick

---

### Post by neu2buntu on 2008-12-27
i think the intel soundcard works best under alsa....so is sound good now ?

---

### Post by neu2buntu on 2008-12-27
mark the post as solved if you think this has solved your problem and dont forget to post a thanks to anyone that bhas helped(found beside edit ,quote, at bottom of their post)...just noticfed the thanks....cheers ...mark as solved tho, to help others)

---

### Post by Dazed_75 on 2009-01-14
I have noticed for a long time that sound volume seems to be low for ubuntu compared to windows on any system on which I run both.  It was never much of a problem until I got an Asus EEE PC 1000 where the sound was barely audible AFTER installing ubuntu.  

NOTE the volume was fine under the Xandros it came with.  I also tried a KNOPPIX 5.1.1 LiveCD and volume was fine there.  Fedora 9 LiveCD gave weak volume just like ubuntu.

This thread gave me the tools to discover and fix the problem.  Apparently, the volume is affected by BOTH the Lineout volume AND the PCM volume.  They interact which I had not expected since I had always thought Lineout was specifically for a line level output jack and not normally volume controlled. WRONG!!!

It appears the Lineout volume can be controlled in alsa and seems to be defaulted to roughly 50%.  So the solution was to raise that normally not visible volume control.

For alsamixer, press the F5 key to show all controls and then you can arrow to the Lineout control and change its setting.

Gnome-alsamixer is even easier since Lineout showed by default.  BTW if you install it using synaptic, gnome-alsamixer gets added to the sound menu.

---

### Post by UJM on 2009-05-11
> **linux_tech said:**
> If you are familiar with using alsamixer, this command will will show all the alsamixer settings


```
alsamixer -D hw:0
```

you can also use Gnome-alsamixer, but you will need to install it first.


```
sudo apt-get install gnome-alsamixer
```

Then to open gnome-alsamixer type



```
gnome-alsamixer
```

check all settings, make sure nothing is muted;
make sure front, master and headphone is checked


If you havn't already installed these under Intrepid, installing these next they will help improve your sound
```
sudo apt-get install alsa-oss

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```


Also to open volume control type:
```


gnome-volume-control

```


I had very low volume on my headphone output, I could barely hear anything! 

alsamixer showed my headphone volume on zero, it wasn't muted, and it refused to be increased.
 
Installing the Gnome-alsamixer and gnome-volume-control fixed this instantly, many thanks!!!

---

