---
title: "ubuntu vlc and wav"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by squrl on 2010-02-05
does vlc play wav files?  It is playing mp3 files just fine but nothing I do seems to help and searching hasn't revealed a thing

thanks

---

### Post by SuperSonic4 on 2010-02-05
Yeah, it does play wav, or at least mine does. 

I tested on VLC 1.1-GIT with a song ripped from an audio CD

Have you checked to see if wavpack is installed

---

### Post by squrl on 2010-02-05
It apparently is an unsupported third party file. Surely ubuntu has cover their bases better than that

---

### Post by benerivo on 2010-02-05
What is the file? Can you share it?

---

### Post by squrl on 2010-02-05
wavpack

---

### Post by andrew.46 on 2010-02-12
Hi squrl,

> **squrl said:**
> does vlc play wav files?

Perhaps as Supersonic has suggested your copy does not. You can test this as follows:

```

andrew@skamandros~$ **[COLOR="Blue"]cvlc -l | grep wav[/COLOR]**
VLC media player 1.1.0-git The Luggage
  wave                   Wave video filter
  **[COLOR="Blue"]wav                    WAV demuxer[/COLOR]**
  mux_wav                WAV muxer

```

All the best,

Andrew

---

### Post by mixmastamyk on 2010-02-12
It plays standard PCM .wav files.  

However, .wav files can also be compressed with old codecs under Windows.  It isn't common, but these files do exist.

There is a posibility they would play with vlc under Windows, not likely on linux.

---

### Post by l-x-l on 2010-02-13
wav & wavpack are 2 different types of files (with wav being more common). Try installing the "wavpack" package in Ubuntu.

---

### Post by Julita on 2010-02-14
You can contact directly the developers of VLC on forum.videolan.org You can  get help there because sometimes VLC has issues with non-standard files, and there you can find more detailed info about the playback of the files.

---

