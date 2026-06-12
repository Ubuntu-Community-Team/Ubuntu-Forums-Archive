---
title: "Talking books to an iPod Nano"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by Scunnered on 2009-05-23
I wish to load talking books (CDs) on to an iPod Nano and would like to know if it can be safely done within Ubuntu?

What programme is available and where may I source it?

---

### Post by blueridgedog on 2009-05-24
The first step is to "rip" the audio files on the CD to MP3 format.  There are many tools for this, and you may have some installed already.  See [http://tldp.org/HOWTO/MP3-HOWTO-7.html](http://tldp.org/HOWTO/MP3-HOWTO-7.html) for example.  Many of the audio players that come with Ubuntu can do it as well.  Banshee (a default audio player) can rip discs if you have lame installed;

```
sudo aptitude install gstreamer0.10-lame lame lame-extras
```

Once ripped, you will have MP3 files on your hard drive.  From there you can send them to your iPod with a variety of programs.  I prefer Floola.

---

### Post by Scunnered on 2009-05-25
Many thanks for your reply.

I will have a look at this tomorrow as the library is closed today. I hope that I can just copy the Audio files over and follow your advise to get them on to the Ipod.

---

