---
title: "No Sound on Sony Vaio"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Belgatom on 2009-09-03
My apologies for posting the same thread again but there was no reply on my previous one. 

I've been running 7.04 for ages on my Vaio TR5EB notebook. At home I installed Jaunty and have been very happy with it. So I wanted to see it implemented on my laptop.

I installed it and everything worked straight out of the box except sound. I remember having problems with the sound when I first installed 7.04 but a friend of mine fixed it so I don't know how. My knowledge of Linux is basic but these forums have always shown me the way, I hope this time, you guys will do that magic thingie again.

Extra info: I don't get sound through headphone jack either.

---

### Post by nothingspecial on 2009-09-03
You need to post your sound card

```
aplay -l
```

---

### Post by Belgatom on 2009-09-03
```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Here it is. Thank you for taking your time.

---

### Post by nothingspecial on 2009-09-03
First type ```
alsamixer
``` and check nothing is muted. Move through the channels with the arrow keys and toggle mute with the M key.

Then try 
```
sudo nano /etc/modprobe.d/alsa-base
``` and adding ```
options snd-intel8x0 ac97_quirk=3
``` to the end. If that doesn`t work remove it.

And (not being rude) check there isn`t a switch you need to press.

---

### Post by Belgatom on 2009-09-03
In Alsa Mixer, I found almost everything was on, I went all the way to the end and found some that were muted but unmuting them didn't change anything. 

I added the line at the bottom of alsa-base.conf and rebooted just to make sure. But no success. I have now removed the line from the alsa-base.conf. 

Don't worry 'bout the switch remark. I work in Support and it's best to first get rid of the most obvious causes. 

Do you have any advice where to go from here?

---

### Post by nothingspecial on 2009-09-03
```
lsmod |grep snd
```

Will tell you which module is controlling your sound. Try googling it with ubuntu or linux. There is usually a fix out there.

---

### Post by Belgatom on 2009-09-03
```
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm

```

What exactly should I google?

---

### Post by nothingspecial on 2009-09-03
Well, I just googled ```
snd_intel8x0 ubuntu I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]   Subdevices: 1/1
```

That is a combination of the card listed by aplay -l and the first module listed by lsmod.

I got some interesting [[COLOR="Magenta"]results[/COLOR]]("http://www.google.co.uk/search?q=snd_intel8x0+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a") but nothing that fixes your sound yet.

If your freind fixed it the answer is out there somewhere.

Good luck

---

### Post by new4me on 2009-09-03
Hey how are ya?
So I just finished solving my sound problem on my Vaio and I thought that I might share what i did.

I tried everything like adding the extra lines to my alsa-base.conf and a whole bunch of other things. The one thing that worked for me was reinstalling ALSA.

go to [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) and download the Driver (alsa-driver) and the library (alsa-lib) version 1.0.21

then open up another tab to the following address [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and go down to the section called "Update to the Latest Version of ALSA" and follow the steps to install the alsa-driver and alsa-lib.

reboot computer and you should be good to go. (I hope)

I also just found this on the forum.
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
its a script to upgrade to the newest version of alsa, but I don't know if it works though

later
J

---

