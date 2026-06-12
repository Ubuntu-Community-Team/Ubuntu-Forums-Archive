---
title: "CD ripping"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by dca on 2010-10-14
I have all the necessary codecs install in Ubuntu 10.10 but when I rip CDs using either Rhyhtmbox or SoundJuicer they all say 128kpbs.  I'm trying for AAC (.m4a) 256kbps (variable bit rate).  Thanks...

---

### Post by jtarin on 2010-10-14
I assume you have all your settings correct.....so here are... [Some other suggestions.]("http://maketecheasier.com/the-ultimate-guide-to-manage-your-audiovideo-files-in-linux/2009/03/03")

---

### Post by cjv8888 on 2010-10-14
> **dca said:**
> I have all the necessary codecs install in Ubuntu 10.10 but when I rip CDs using either Rhyhtmbox or SoundJuicer they all say 128kpbs.  I'm trying for AAC (.m4a) 256kbps (variable bit rate).  Thanks...

Not sure about AAC but I get 256kbps in mp3 by editing the gstreamer pipeline to:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=0 bitrate=256 ! id3v2mux
```

In AAC, you might have to edit the faac profile=2 to another number or delete it altogether and replace it with bitrate=256

Hope that helps.

---

### Post by dca on 2010-10-14
Great, thanks... I'll try that...

---

