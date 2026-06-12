---
title: "Can't watch movies!"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by GodlySoup on 2009-09-12
Trying to open it with the default movie player that Jaunty came with. It says I don't have enough privileges. 

Please help!

---

### Post by Perfect Storm on 2009-09-12
You have installed all the codecs and restricted libs to run Movies and DVD?
Other than that I suggest you get your hands on VLC, it never failed me.

---

### Post by jmszr on 2009-09-12
GodlySoup,

If you haven't already you will need to install Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then you will need to install:```
sudo apt-get install libdvdcss2
```

and if you haven't yet```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by agaray on 2009-09-12
Make sure you have read access to the file you're trying to play. Install the codecs as suggested. gstreamer-plugins-good, bad, ugly, ffmpeg. You'll also want libdvdread, libdvdnav, libdvdcss (check local laws), and w32codecs (w64codecs).

---

### Post by armandh on 2009-09-12
on a new install I always go to [www.medibuntu.org](www.medibuntu.org) and follow the how to [a few easy copy and paste to terminal.]

then I get the VLC player

---

### Post by talsemgeest on 2009-09-12
> **armandh said:**
> on a new install I always go to [www.medibuntu.org](www.medibuntu.org) and follow the how to [a few easy copy and paste to terminal.]

then I get the VLC player
For normal videos I would suggest installing the Ubuntu restricted extras: ```
sudo apt-get install ubuntu-restricted-extras
``` which will install all the codecs to view almost any video file. For encrypted dvds (the kind you would buy off the shelf), you should follow this how-to: [http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands](http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands)

---

