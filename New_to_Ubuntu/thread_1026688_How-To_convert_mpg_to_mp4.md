---
title: "How-To convert mpg to mp4"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by cerealtx on 2008-12-31
trying to convert mpgs to mp4 for ipod can't find anything have done numerous google searches

---

### Post by retskrad on 2008-12-31
Try [www.media-convert.com](www.media-convert.com).

---

### Post by emecas on 2008-12-31
> **cerealtx said:**
> trying to convert mpgs to mp4 for ipod can't find anything have done numerous google searches

you can use : mencoder


sudo apt-get install mencoder


Script:

* from mpeg to mpeg4

      #!/bin/sh
      # usage: mpg2mp4.sh your_mpg your_avi
      VBITRATE=500

      mencoder "$1" -ovc frameno -o frameno.avi -oac mp3lame -lameopts vbr=3
      mencoder "$1" -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=$VBITRATE:vpass=1 -oac copy -o "$2"
      mencoder "$1" -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=$VBITRATE:vpass=2 -oac copy -o "$2"

      rm -f frameno.avi
      rm -f *.log



source: [http://blog.roodo.com/thinkingmore/archives/2006-08.html&page=1](http://blog.roodo.com/thinkingmore/archives/2006-08.html&page=1)

---

### Post by wolfen69 on 2008-12-31
[Handbrake]("http://handbrake.fr/?article=download") is the easiest solution. 1 click. there are presets (on the right of the app) for ipods.

---

### Post by bumanie on 2008-12-31
Winff is another option - it codes to various formats for various devices. It is basically a GUI for ffmpeg.

---

