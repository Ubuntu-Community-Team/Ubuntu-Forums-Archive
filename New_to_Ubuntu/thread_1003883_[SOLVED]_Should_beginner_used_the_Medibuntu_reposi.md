---
title: "[SOLVED] Should beginner used the Medibuntu repository"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by linuxford on 2008-12-06
I've heard the Medibuntu repository (medibuntu.org) is good to add for multimedia software, but it not being official wasn't sure if I should. Any gotchas that a newbie might have difficulties addressing by adding it, or is no more risk than the main repositories.

---

### Post by binbash on 2008-12-06
you should add medibuntu repository.It is easy to add

---

### Post by hyper_ch on 2008-12-06
medibuntu is save to add... just go ahead and add it.

---

### Post by Flimm on 2008-12-06
What do you need medibunutu's repository for? Most of the stuff I want that's not available in the repos is found on [getdeb](http://www.getdeb.net).

---

### Post by 2hot6ft2 on 2008-12-06
Personally I use it. It's all up to you and what you want to do. If you want all open source then don't. If you want to be able to use flash, shockwave, watch dvd's, avi's mp3's, and all those types of things then you'll end up using some proprietary codecs.

If you decide to use them then I suggest this guide [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by hyper_ch on 2008-12-06
flimm: better to use a repo than a .deb from some place ;)

---

### Post by evilkastel on 2008-12-06
Is not just safe, is great. If you have any aspirations of geting video, music, youtube, or java apps in your box you should add it and install ubuntu-restricted-extras among other useful packages.

---

### Post by s.fox on 2008-12-06
nI use it and have had no problems with it.  I didn't really care about the open source idea for my media,  i just wanted to watch my dvd's.

---

### Post by detroit/zero on 2008-12-06
> **Flimm said:**
> What do you need medibunutu's repository for?
Adobe Reader and Flash, DVD playback, Google Earth, Skype, RealPlayer, win32 codecs, msttcorefonts, and about a million other things that aren't right on the tip of my tongue.

---

### Post by wolfen69 on 2008-12-06
> **detroit/zero said:**
> Adobe Reader and Flash, DVD playback, Google Earth, Skype, RealPlayer, win32 codecs, msttcorefonts, and about a million other things that aren't right on the tip of my tongue.

medibuntu repos are not needed for flash, java, codecs and dvd playback. but you may want it for the other things mentioned.

---

### Post by OrangeCrate on 2008-12-06
If you haven't already found the instructions, here's how to add Medibuntu...

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

(And, don't forget to add the GPG key.)

---

### Post by linuxford on 2008-12-06
> **OrangeCrate said:**
> (And, don't forget to add the GPG key.)

Cool.. thanks everyone.  

Question: This GPG key, is this what you are talking about [http://ubuntuforums.org/showthread.php?t=998144&highlight=gpg]("http://ubuntuforums.org/showthread.php?t=998144&highlight=gpg")

And if it is some sort of encryption/decryption is needed, just curious why I need this? Is it specifically dealing with repositories? or package? or just in general I should get it?

---

### Post by OrangeCrate on 2008-12-06
> **linuxford said:**
> Cool.. thanks everyone.  

Question: This GPG key, is this what you are talking about [http://ubuntuforums.org/showthread.php?t=998144&highlight=gpg]("http://ubuntuforums.org/showthread.php?t=998144&highlight=gpg")

And if it is some sort of encryption/decryption is needed, just curious why I need this? Is it specifically dealing with repositories? or package? or just in general I should get it?

There's lots of different kinds of keys. If you install the Medibuntu one, it just tells your computer that Medibuntu is a safe software source. The key will show up in the "Trusted software sources" tab in "Software Sources" on your computer.

(Administration > Software Sources)

Just follow the instructions to install, that I gave you in my last post ^.

---

### Post by detroit/zero on 2008-12-07
> **wolfen69 said:**
> medibuntu repos are not needed for flash, java, codecs and dvd playback. but you may want it for the other things mentioned.
Well, you got me on Flash and Java:
```
**Binary packages available in hardy**

     
[LIST]
[*]
[*][aacplusenc]("http://packages.medibuntu.org/hardy/aacplusenc.html")
[*]
[*][acroread-escript]("http://packages.medibuntu.org/hardy/acroread-escript.html") 
[*][acroread]("http://packages.medibuntu.org/hardy/acroread.html") 
[*][acroread-plugins]("http://packages.medibuntu.org/hardy/acroread-plugins.html")
[*]
[*][alsa-firmware]("http://packages.medibuntu.org/hardy/alsa-firmware.html")
[*][amarok-engines]("http://packages.medibuntu.org/hardy/amarok-engines.html")
[*][amarok]("http://packages.medibuntu.org/hardy/amarok.html")
[*][amarok-xine]("http://packages.medibuntu.org/hardy/amarok-xine.html")
[*][amrnb]("http://packages.medibuntu.org/hardy/amrnb.html")
[*][amrwb]("http://packages.medibuntu.org/hardy/amrwb.html")
[*][ffmpeg]("http://packages.medibuntu.org/hardy/ffmpeg.html")
[*][googleearth-4.2-data]("http://packages.medibuntu.org/hardy/googleearth-4.2-data.html")
[*][googleearth-4.2]("http://packages.medibuntu.org/hardy/googleearth-4.2.html")
[*][googleearth-4.3-data]("http://packages.medibuntu.org/hardy/googleearth-4.3-data.html")
[*][googleearth-4.3]("http://packages.medibuntu.org/hardy/googleearth-4.3.html")
[*][googleearth]("http://packages.medibuntu.org/hardy/googleearth.html")
[*][hot-babe]("http://packages.medibuntu.org/hardy/hot-babe.html")
[*][ibm-j2re1.5]("http://packages.medibuntu.org/hardy/ibm-j2re1.5.html")
[*][ibm-j2re1.6]("http://packages.medibuntu.org/hardy/ibm-j2re1.6.html")
[*][ibm-j2sdk1.5]("http://packages.medibuntu.org/hardy/ibm-j2sdk1.5.html")
[*][ibm-j2sdk1.6]("http://packages.medibuntu.org/hardy/ibm-j2sdk1.6.html")
[*][libamrnb3]("http://packages.medibuntu.org/hardy/libamrnb3.html")
[*][libamrnb-dev]("http://packages.medibuntu.org/hardy/libamrnb-dev.html")
[*][libamrwb3]("http://packages.medibuntu.org/hardy/libamrwb3.html")
[*][libamrwb-dev]("http://packages.medibuntu.org/hardy/libamrwb-dev.html")
[*][libavcodec1d]("http://packages.medibuntu.org/hardy/libavcodec1d.html")
[*][libavcodec-dev]("http://packages.medibuntu.org/hardy/libavcodec-dev.html")
[*][libavformat1d]("http://packages.medibuntu.org/hardy/libavformat1d.html")
[*][libavformat-dev]("http://packages.medibuntu.org/hardy/libavformat-dev.html")
[*][libavutil1d]("http://packages.medibuntu.org/hardy/libavutil1d.html")
[*][libavutil-dev]("http://packages.medibuntu.org/hardy/libavutil-dev.html")
[*][libdvdcss2-dev]("http://packages.medibuntu.org/hardy/libdvdcss2-dev.html")
[*][libdvdcss2]("http://packages.medibuntu.org/hardy/libdvdcss2.html")
[*][libpostproc1d]("http://packages.medibuntu.org/hardy/libpostproc1d.html")
[*][libpostproc-dev]("http://packages.medibuntu.org/hardy/libpostproc-dev.html")
[*][libswscale1d]("http://packages.medibuntu.org/hardy/libswscale1d.html")
[*][libswscale-dev]("http://packages.medibuntu.org/hardy/libswscale-dev.html")
[*][medibuntu-keyring]("http://packages.medibuntu.org/hardy/medibuntu-keyring.html")
[*][mencoder]("http://packages.medibuntu.org/hardy/mencoder.html")
[*][mozilla-acroread]("http://packages.medibuntu.org/hardy/mozilla-acroread.html")
[*][mplayer-doc]("http://packages.medibuntu.org/hardy/mplayer-doc.html")
[*][mplayer]("http://packages.medibuntu.org/hardy/mplayer.html")
[*][mplayer-nogui]("http://packages.medibuntu.org/hardy/mplayer-nogui.html")
[*][non-free-codecs]("http://packages.medibuntu.org/hardy/non-free-codecs.html")
[*][ppc-codecs]("http://packages.medibuntu.org/hardy/ppc-codecs.html")
[*][skype-common]("http://packages.medibuntu.org/hardy/skype-common.html")
[*][skype]("http://packages.medibuntu.org/hardy/skype.html")
[*][skype-static]("http://packages.medibuntu.org/hardy/skype-static.html")
[*][skype-static-oss]("http://packages.medibuntu.org/hardy/skype-static-oss.html")
[*][w32codecs]("http://packages.medibuntu.org/hardy/w32codecs.html")
[*][w64codecs]("http://packages.medibuntu.org/hardy/w64codecs.html")
```
[/LIST]

---

