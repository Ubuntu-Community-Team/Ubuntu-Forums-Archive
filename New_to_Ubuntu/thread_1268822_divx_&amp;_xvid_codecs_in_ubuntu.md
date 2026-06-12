---
title: "divx &amp; xvid codecs in ubuntu ?"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by Fatalrewind on 2009-09-17
I am trying to play a recent movie in movie player but i get a blank
screen and vlc player shows a splash screen telling me i need to update
and use moviexplayer.

how do i install the divx and xvid codecs for use ?

thanks

please note ,i have read up on his and found my video file to
be a scam ,fake file that would only play with moviexplayer.

---

### Post by wildman4god on 2009-09-17
you could look in add/remove to find them but a better way is to install all the codecs at once by installing the ubuntu restricted extras package, this not only installs all codecs except encrypted dvd playback but also installs ms fonts, flash, jave, etc. basically every thing you need for compatiblity.

First make sure you have Medibuntu repositories enabled, there is a tutorial [here]("http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/")

then copy and paste this code into a terminal

```
sudo apt-get install ubuntu-restricted-extras
```

enjoy.

or just go [here]("http://appnr.com/package/gstreamer0.10-plugins-bad-multiverse") and click install (this will install the specific codecs your looking for not all of them).

---

### Post by SunnyRabbiera on 2009-09-17
Yeh by default Ubuntu cannot provide these codecs due to legal BS, but with medibuntu and ubuntu restricted extras enabled it will help you get playback

---

### Post by NightwishFan on 2009-09-17
I think it is awesome how Gstreamer handles playback. In Windows you install some odd "Codec Pack" to get playback. In Gstreamer you just have integrated plugins to enable decoding and encoding, and it even has a command-line backend called gst-launch. It even installs some plugins automatically when needed.

---

