---
title: "Sound problems"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by susanpenter on 2009-02-28
I am having sound problems for a second time. Last time I had to install flash 10 and it works this time I can't find a solution.

The intro music plays load and clear but there is no other sounds either through the internet or Amarok.  Amarok says "xine was unable to initialize any audio drivers" but there must be some audio drivers for the intro music to play....

If anyone can help I'd be grateful

---

### Post by NoReflex on 2009-02-28
I removed PulseAudio and I'm using Alsa. You can configure this in Multimedia Systems Selector.

Best wishes,
NoReflex

---

### Post by susanpenter on 2009-03-02
I'm feeling rather stupid at the moment but I can't find a file in the control panel or anywhere called Multimedia systems selector.

Whether it is related but my movie player will no longer play films either (picture or sound)

---

### Post by NoReflex on 2009-03-03
It should be in System -> Preferences. If you can't find it there you can open a terminal, type gstreamer-properties and ENTER.
If it gives a message that it doesn't recognize the command you can (re)install the gnome-media package with Synaptic.

Best wishes,
NoReflex

---

### Post by linux_tech on 2009-03-03
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type


```
gnome-alsamixer

```
check all settings, make sure nothing is muted


To open volume control type:
```
gnome-volume-control

```

---

### Post by Sirron on 2009-03-03
Before removing Pulse Audio, it might be worth checking you have amarok configured correctly. Follow the instructions [_here_]("http://www.pulseaudio.org/wiki/PerfectSetup#Amarok").

---

### Post by susanpenter on 2009-03-11
I have tried all these suggestions and nothing has worked.  I still only get the soundfile that plays at boot up, nothing through Amarok and nothing over the internet.

I'm wondering whether I could have too many drivers, ther is a few saying ATI, ALSA, EDS, OSS and Pulse Audio listed.

---

### Post by kansasnoob on 2009-03-11
I'd run through the Intrepid specific steps, and then if needed the Troubleshooting section, here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by susanpenter on 2009-03-12
> **kansasnoob said:**
> I'd run through the Intrepid specific steps, and then if needed the Troubleshooting section, here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I have run through all the steps found here and now my opening theme music has stopped playing so in fact it has all become even worse.......


Are there any other suggestions....:confused:

---

### Post by NoReflex on 2009-03-12
I remember I had to reinstall alsa from source when sound didn't work in Ubuntu Edgy.
Maybe it will work for you too.

Best wishes,
NoReflex

---

### Post by susanpenter on 2009-03-12
I have tried that and once again no change....

---

### Post by NoReflex on 2009-03-12
This is really odd...
Please try to boot the Ubuntu Live CD (or another Live CD) and check if your sound system works.
Good luck!

Best wishes,
NoReflex

---

### Post by susanpenter on 2009-03-12
Hurray I have sound! With my pc I have a set of speakers within the monitor that came with it and a seperate set of Creative ones. The speakers built in to the monitor are not producing any sound - but when I pluged the Creatives in again (I had borrowed them to use with the laptop for a project) the sound worked.  Still a mystery about the other speakers though....

---

