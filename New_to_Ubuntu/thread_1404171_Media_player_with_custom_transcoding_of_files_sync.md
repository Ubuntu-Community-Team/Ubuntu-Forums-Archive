---
title: "Media player with custom transcoding of files synced to MTP device"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by kkjaergaard on 2010-02-11
Since my music collection is in FLAC, I would like my media player to transcode the media files. Is there a media player that lets me decide what codec/bitrate to convert to?

---

### Post by aryan22 on 2010-02-11
soundconverter
 ```
sudo apt-get install soundconverter
```
 
 you'll need to install gstreamer ugly plugin for mp3 support
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by kkjaergaard on 2010-02-12
> **aryan22 said:**
> soundconverter...

It does not support MTP. And it is not a media player.

All I want is my media player to automatically convert a FLAC file to an OGG file (using e.g. oggenc) before synchronizing the file to my portable media player.

---

