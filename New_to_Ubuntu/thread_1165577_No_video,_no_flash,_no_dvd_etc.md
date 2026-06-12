---
title: "No video, no flash, no dvd etc"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by HarleyDude on 2009-05-20
Ok, don't yell at me.  I have loaded 9.04 amd64 on my hp dv8000.  I finally got the wireless working and everything seems to work fine except I cannot get video of any sort to work.  I have followed the multi step instructions but I still cannot get any of it to work.  Where do I go next, getting tired.

---

### Post by perlluver on 2009-05-20
Have you installed ubuntu-restricted-extras?  Also go to [http://www.medibuntu.org](http://www.medibuntu.org), and follow the instructions there for DVD's and Windows Codecs.  I would also recommend VLC you can find it under Applications>Add/Remove.

---

### Post by HarleyDude on 2009-05-20
I'll give it a try and let you know.

---

### Post by HarleyDude on 2009-05-20
Yes, I had already installed (I think) even the libdvdcss2 and W64 codecs

---

### Post by Zzl1xndd on 2009-05-20
Can you give a little more detail on what is happening when you attempt to play a Video? Are the players not opening, or are they just displaying a black screen?

---

### Post by HarleyDude on 2009-05-20
If I pop in a dvd, the player eventually just says missing the correct plug-in, asks me if I want to search etc, when online, tried a youtube and it tells me I need the player but can't get it installed, always says I have the wrong archetechure.

---

### Post by Zzl1xndd on 2009-05-20
Try VLC for the DVD to see if we have any better results.

As for you tube did you install 32bit Ubuntu or 64?

---

### Post by glennric on 2009-05-20
Do you have totem-xine or totem-gstreamer installed?  I have never been able to get totem-gstreamer to work properly with dvd's.  totem-gstreamer is the default that is installed with Ubuntu.  If you still have that installed try installing totem-xine, and then uninstalling totem-gstreamer.

---

### Post by HarleyDude on 2009-05-20
64 bit

---

### Post by Zzl1xndd on 2009-05-20
I'm not sure the 64bit version of Flash is in the Repositories you may want to try downloading it from the adobe site.

---

### Post by HarleyDude on 2009-05-20
I did try to install the 64bit flash player without success.  I looked for VLC and it is not listed that that I can tell

---

### Post by presence1960 on 2009-05-20
did you install Flash? Here is the 64bit install how to for Flash: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) This is way simpler than getting from Adobe's site. This is Adobe Flash though, check it out.

---

### Post by presence1960 on 2009-05-20
> **HarleyDude said:**
> I did try to install the 64bit flash player without success.  I looked for VLC and it is not listed that that I can tell

open a terminal and run : ```
sudo apt-get install vlc
```

---

### Post by HarleyDude on 2009-05-20
VLC is working, now on to the flash.

---

### Post by dipaish on 2009-05-20
Try this one : 

go to terminal and type 

sudo apt-get install ubuntu-restricted-extras

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

---

### Post by HarleyDude on 2009-05-20
Thanks to everyone that chimed in!  All it took was a little more help and as of now it all, I repeat all works, from dvd's to youtube to audio it is all up and running.  Thanks again, very much appreciated!

---

### Post by presence1960 on 2009-05-20
> **HarleyDude said:**
> Thanks to everyone that chimed in!  All it took was a little more help and as of now it all, I repeat all works, from dvd's to youtube to audio it is all up and running.  Thanks again, very much appreciated!

Excellent!! :popcorn:

---

### Post by Zzl1xndd on 2009-05-20
Glad we could help.

---

