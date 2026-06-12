---
title: "Software"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by DGINSD on 2011-02-28
I've noticed some of the programs downloaded from the repositorys that came with my Ubuntu install don't work as advertised is there something I'm missing, specifically display calibration apps. and multimedia players.

Also I've learned you can add other repositorys what are some other useful and trusted ones you all would recommend?

---

### Post by Frogs Hair on 2011-02-28
I'm not sure about your dispaly settings . Do you have media plug-ins installed ? if not install Ubuntu restricted extras . The package includes audio an video plug-ins

---

### Post by stoneage on 2011-02-28
Can you state specifically which programs and how they do not work?
Ideally include any error messages.

---

### Post by aeiah on 2011-02-28
most media players in ubuntu dont play the audio or video themselves, they rely on codecs and frameworks, and this could likely be the problem. because a lot of media decoders are patent encumbered, they aren't shipped with ubuntu by default and are in the aformentioned 'restricted extras' repository, or are available through the medibuntu repo.

most software in ubuntu relies on other software, so called 'dependencies', and usually any dependencies are installed automatically for you when you use the software center or synaptic - they just arent with codecs due to what i described.

---

### Post by DGINSD on 2011-02-28
At work now on my phone but I'll list more details (stupid me "help me help you" right) when I get home and back together with my great new "toy"

I have installed the restricted packages and a bunch of other things to try and get everything playing nicely together. So far only one media player works good Gnome Mmedia player I think its called, and I had to chang some settings to get that to work. 

Any Ideas on some other good places to get more free goodies?  I'd even settle for cheap goodies?

---

### Post by The Linux Cynic on 2011-02-28
So you want a good video player and no headaches with codecs, etc?

**[VLC]("http://www.videolan.org/").**

In terminal:
```
sudo apt-get update
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
```

---

### Post by IWantFroyo on 2011-02-28
Welcome to Linux! This is where Ubuntu rocks. There are codecs available for just about all media types.
The good ones: VLC (just type vlc into software center, or do above, although try reversing the order of those two commands)
Xine (the main .wma player)
Rhythmbox (although you can get a free download of iTunes from Apple and use Wine to open it)
If you have a webcam, cheese is really nice (software center)
Unrelated Linux goodies I fell for:
Gnumeric (Software Center)
LibreOffice (search libreoffice, then find a guide on the internet to install)
Google Earth (earth.google.com- be sure to run sudo apt-get install lsb-core or it won't work)
Chromium
GIMP
Inkscape
Skype
Eclipse
AWN
The list goes on...

---

### Post by DGINSD on 2011-02-28
> **IWantFroyo said:**
> Welcome to Linux! This is where Ubuntu rocks. There are codecs available for just about all media types.
The good ones: VLC (just type vlc into software center, or do above, although try reversing the order of those two commands)
Xine (the main .wma player)
Rhythmbox (although you can get a free download of iTunes from Apple and use Wine to open it)
If you have a webcam, cheese is really nice (software center)
Unrelated Linux goodies I fell for:
Gnumeric (Software Center)
LibreOffice (search libreoffice, then find a guide on the internet to install)
Google Earth (earth.google.com- be sure to run sudo apt-get install lsb-core or it won't work)
Chromium
GIMP
Inkscape
Skype
Eclipse
AWN
The list goes on...

No doubt I'm like a kid in a candy store!

I love the Chromium browser (still playin with it though)

VLC player is one of the ones I'm havin problems with. Read a post sayin it was one of the better ones, but DVD playback is very choppie

---

### Post by DGINSD on 2011-03-01
Got VLC player to work last night had to change the video output mode to X11 just like I did Gnome mplayer but the sound keeps going in and out, actually I've noticed a lot of quirky little bugs with this system for example I set the system up to hibernate when the lid closes but yesterday before I left for work it wouldn't hibernate it just stayed on so I went to shut down and it started to but it stopped with the power still on but nothing displaying or working. Another issue is occasionally my monitor will just blink out. My computer is a Dell Inspiron 1150. I was wondering if that has any thing o do with the display settings programs and color control applets not doing anything?

---

