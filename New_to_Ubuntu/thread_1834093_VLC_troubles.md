---
title: "VLC troubles"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by trouseregime on 2011-08-27
Hi all,

I recently installed pacpl to do some audio conversions and evidently it deleted a bunch of files including VLC. Reinstalling VLC is now being troublesome and I'm getting a host of error messages. 

When I try with Software Centre it says:

Package dependencies cannot be resolved

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.8) but 1.0.6-1ubuntu1.8 is to be installed
     Depends: libaa1 (>= 1.4p5) but 1.4p5-38build1 is to be installed
     Depends: libc6 (>= 2.8) but 2.13-0ubuntu13 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.4-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
     Depends: libglib2.0-0 (>= 2.12.0) but 2.28.6-0ubuntu1 is to be installed
     Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.4-0ubuntu2 is to be installed
     Depends: libnotify1-gtk2.10 but it is a virtual package
     Depends: libqtcore4 (>= 4:4.6.1) but 4:4.7.2-0ubuntu6 is to be installed
     Depends: libqtgui4 (>= 4:4.6.1) but 4:4.7.2-0ubuntu6 is to be installed
     Depends: libsdl-image1.2 (>= 1.2.5) but 1.2.10-2ubuntu1 is to be installed
     Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.14-6.1ubuntu3 is to be installed
     Depends: libstdc++6 (>= 4.2.1) but 4.5.2-8ubuntu4 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed



I've also tried with Synaptic and get turned away from installing the various VLC bits telling me that I don't have the necessary parts and leads me to other sections until I get to libvlccore2 at which point it tells me: 

libvlccore2:
  Depends: vlc-data (=1.0.6-1ubuntu1.8) but 1.1.9-1ubuntu1 is to be installed



Any thoughts on how I can get my precious VLC back?

Thanks

On a side note, I've been using sound converter to get from .flac and .m4a to .wav but the tags don't stick to the converted file which is a massive pain. Anyone know any programs which will keep the tags on the converted file?

---

### Post by Chronon on 2011-08-27
Have you modified the software sources?

Regarding converting to WAV: This is basically just PCM with a simple RIFF header.  You can't embed metadata in it.  Why would you want to convert from FLAC to WAV anyway?  It is double the size for the same audio and no support for metadata.

---

### Post by trouseregime on 2011-08-27
I guess not necessarily .wav, just something lossless that I can put on my ipod. 

I'm not aware of having modified the software sources. I'm very new to all of this.

---

### Post by Chronon on 2011-08-27
If you post the contents of /etc/apt/sources.list here it might reveal something.  It seems that there's an inconsistency between versions of software on your system.  Have you manually installed any software?  Usually this shouldn't occur if you are installing software from the Software Center.

Unfortunately, iPods only support WAV, AIFF and ALAC for lossless formats.  ALAC is actually an MP4 file containing a lossless audio stream, so it can contain rich metadata, unlike AIFF or WAV. I have seen rumors that ffmpeg has an ALAC encoder, but I haven't investigated it myself.

---

### Post by trouseregime on 2011-08-27
This is what appears... A friend of mine has set this up for me, so I'm not entirely sure what the following entails.

deb [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) lucid main restricted uni$
deb [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) lucid-updates main restri$
deb [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) lucid-security main restr$

---

### Post by trouseregime on 2011-08-27
A large chunk of my music is in ALAC, but I can't seem to find a program on Ubuntu that will put these files onto my iPod. I think I'll just convert to mp3 so as to keep the tags and just deal with lossy music on the go. The speakers and headphones I use them with aren't so brilliant anyway.

---

