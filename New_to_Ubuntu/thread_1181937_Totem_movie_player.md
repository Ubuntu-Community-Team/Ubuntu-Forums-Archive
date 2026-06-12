---
title: "Totem movie player"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by nobodygh on 2009-06-08
I've recently installed Ubuntu 9.04, Jaunty, on my desktop, I'm really enjoying the break from Windows and all the cool perks like Wanda the Fish and those eyes that follow your pointer around. But I'm experiencing a few problems with the media player...

Whenever I open a file in Totem it quits immediately.

I run Totem Movie player 2.26.1 and that uses GStreamer 0.10.22 and I've installed a few codecs(not sure which ones).

Any help would be welcome

thank you

---

### Post by bumanie on 2009-06-08
Follow [this]("https://help.ubuntu.com/community/Medibuntu") to ensure you have all the necessary codecs algorithms to play proprietary cd's/dvd's

---

### Post by UbuntuNerd on 2009-06-08
check out this quick and simple [guide](http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem)

---

### Post by NightwishFan on 2009-06-08
Press alt+f2 and type:
```
gstreamer-properties
```

Under the video tab, change the output to (i think x11 video) something like that. I cannot remember the exact name. (I am on Windows now).

Try to play a video, if it works now, that means your display adapter (likely intel) does not support video hardware acceleration, and will need to wait for newer drivers.

---

