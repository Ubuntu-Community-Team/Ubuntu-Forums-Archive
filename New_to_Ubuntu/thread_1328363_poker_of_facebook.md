---
title: "poker of facebook"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by godsmAsh on 2009-11-16
hi, 
 i use Ubuntu 9.10 and has gnash installed and yet i can't play poker on facebook. how can i solve this problem.

---

### Post by blazemore on 2009-11-16
To be quite honest, gnash just doesn't cut it.
If I were you I would remove gnash and install the Adobe one.
```
sudo apt-get remove gnash && sudo apt-get install flashplugin-nonfree
```

---

### Post by godsmAsh on 2009-11-17
is  "flashplugin-nonfree" free???

someone told me to install ubuntu-restricted-extras.  do you know the code to install this software

---

### Post by fromthehill on 2009-11-17
> **godsmAsh said:**
> is  "flashplugin-nonfree" free???

someone told me to install ubuntu-restricted-extras.  do you know the code to install this software
nonfree means it isn't open-source
it is free as in "doesn't cost money"

ubuntu-restricted extra's installs flash and a bunch of other things

to install ubuntu restricted extras:
sudo apt-get install ubuntu-restricted-extras

"Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio
files), and DVD playback."

---

### Post by muteXe on 2009-11-17
Nice double post.

---

### Post by godsmAsh on 2010-01-02
download adobe flash player 10.1 from adobe site. it works

---

