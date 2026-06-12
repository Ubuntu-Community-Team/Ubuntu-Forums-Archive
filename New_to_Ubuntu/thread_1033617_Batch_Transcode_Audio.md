---
title: "Batch Transcode Audio"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Thelasko on 2009-01-07
Does anybody know of a good way to batch transcode audio files?  I have a bunch of FLAC files that I need to transcode so they are compatible with my mp3 player.  I want all of the files to have the same name as the original ones, except with the .mp3 suffix of course.

I've transcoded a few files with VLC but it's very tedious, I'm wondering if there is a faster way.

---

### Post by unutbu on 2009-01-07
I don't have any flac files to test this out on, but the following might work. 
```

sudo apt-get install ffmpeg
for file in *; do ffmpeg -i $file "${file//.flac/.mp3}"; done
```

Installing ffmpeg takes up about 2084 KiB. 
The second command uses ffmpeg to convert flacs to mp3.
It works on the files in the current working directory.

---

### Post by nothingspecial on 2009-01-07
[flac2mp3]("http://bytemonkey.org/projects/flac2mp3/") is exactly what you`re looking for.

---

### Post by ajgreeny on 2009-01-07
If you want a gui try soundconverter or soundkonverter.

---

### Post by Thelasko on 2009-01-08
I was expecting to need a script or something, but soundconverter exceeded my expectations.  It's a really slick program.

---

