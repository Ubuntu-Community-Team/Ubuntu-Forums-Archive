---
title: "Amarok"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by jnmjr on 2010-04-26
Hey music lovers, I installed Amarok and it plays just about everything except .M4P (MP4) files, is it possible to get it to play these files? Are there codecs available?....THX

---

### Post by NightwishFan on 2010-04-26
Try installing libxine1-ffmpeg. [Click Here To Install]("apt://libxine1-ffmpeg")
or
```
sudo aptitude install libxine1-ffmpeg
```

---

### Post by jnmjr on 2010-04-26
> **NightwishFan said:**
> Try installing libxine1-ffmpeg. [Click Here To Install]("apt://libxine1-ffmpeg")
or
```
sudo aptitude install libxine1-ffmpeg
```

Yes it's installed but I just lost sound on everything again:confused:

---

### Post by NightwishFan on 2010-04-26
That is just codecs, it shouldn't make you lose sound. Try logging out and back in.

---

### Post by jnmjr on 2010-04-26
> **NightwishFan said:**
> That is just codecs, it shouldn't make you lose sound. Try logging out and back in.

Yes what i meant to say it was already installed.... I lost sound for another reason and after a re-start it came back...I still can't play MP4's.

---

### Post by oleink on 2010-04-26
m4a is not supported on amarok.  Try banshee.  It uses gstreamer.  The only thing is m4a is not supported initially.  You gotta find the appropriate gstreamer plugin probably in synaptic

---

### Post by oleink on 2010-04-26
PS I believe amarok uses a thing called "ARTS" but I'm not entirely sure and if it does you can change it to gstreamer somehow but I am not sure how and install the m4a plugin for amarok too and not switch to banshee but banshee alreaedy has gstreamer

---

### Post by jnmjr on 2010-04-26
> **oleink said:**
> m4a is not supported on amarok.  Try banshee.  It uses gstreamer.  The only thing is m4a is not supported initially.  You gotta find the appropriate gstreamer plugin probably in synaptic

M4a is supported, it's M4P (MP4) I was asking about.

---

### Post by oleink on 2010-04-26
Well you took it off an ipod. m4a is apple's extension to mp4 (the officail type)
m4p is their itunes extension.  Both are apple's way of trying to get people to not be able to use other devices or operating systems

---

### Post by oleink on 2010-04-26
PS theyre pretty much the same thing (apple's work of being proprietary) if you can crack one you can crack the other(pretty much except that the one youre looking at is DRM protected my bad)
 
Welcome to the world of Apple

---

### Post by jnmjr on 2010-04-26
> **oleink said:**
> Well you took it off an ipod. m4a is apple's extension to mp4 (the officail type)
m4p is their itunes extension.  Both are apple's way of trying to get people to not be able to use other devices or operating systems

Sorry, my mistake, I guess M4P is not the same as MP4, I'm not up to date with all this music stuff, I'm a CD guy, this is the first time I even play around with an IPOD, I see you are following my other post with Spydey, hopefully we'll have a solution to this whole thing soon...:lolflag:

---

### Post by jnmjr on 2010-04-26
BTW....Is there a specific ppa Amarok needs to be updated? I use Ubuntu and Amarok is KDE so I don't really know....THX

---

### Post by oleink on 2010-04-27
> **jnmjr said:**
> BTW....Is there a specific ppa Amarok needs to be updated? I use Ubuntu and Amarok is KDE so I don't really know....THX

Not that I've found.  I found a ppa for banshee but Amarok ppa's that I've found have all been for beta releases

---

### Post by oleink on 2010-04-27
> **jnmjr said:**
> Sorry, my mistake, I guess M4P is not the same as MP4, I'm not up to date with all this music stuff, I'm a CD guy, this is the first time I even play around with an IPOD, I see you are following my other post with Spydey, hopefully we'll have a solution to this whole thing soon...:lolflag:

M4P is actually apple's extension to the mp4 format.  I don't know why they made the extension this way some people say they simply typed the wrong format (m4p vs mp4) when they first started messing with mp4 formatting and they never changed it but for a company like that I believe they were just trying to continue being proprietary

---

### Post by wall0159 on 2010-05-19
A lot of what has been written in this thread is incorrect.

m4a is the standard extension used by Apple for their AAC-encoded files. Amarok can play these fine, when the appropriate software is installed. Amarok does not necessarily use Arts (eg. when installed from Gnome it does not).

When iTunes was using DRM, those files had the extension m4p. These files can only be played by iTunes and on iPods. I doubt that any open-source software will _ever_ play these files.

I use Amarok 1.4, but for some reason, its ability to play m4a files has ceased since upgrading to Lucid Lynx. I'm not sure why that is...

---

