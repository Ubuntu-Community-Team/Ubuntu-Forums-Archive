---
title: "How can  convert flv to 3gp in ubuntu"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Achu S Sooraj on 2011-02-10
How can convert a flv video file to 3gp video . This is for nokia mobile phone.

pls help me friends

---

### Post by Najmudin on 2011-02-10
Try "Arista Transcoder" you can find it in Ubuntu software center if you are using ubuntu 10.10.

---

### Post by Achu S Sooraj on 2011-02-10
> **Najmudin said:**
> Try "Arista Transcoder" you can find it in Ubuntu software center if you are using ubuntu 10.10.

i install Arista Transcoder but not got output. it need more plug -in from unsafe source. ubuntu not allow it.


pls help me

---

### Post by Najmudin on 2011-02-10
What exactly is the message you are getting?

---

### Post by msharmony2001 on 2013-01-12
> **Najmudin said:**
> Try "Arista Transcoder" you can find it in Ubuntu software center if you are using ubuntu 10.10.
I can find just about every conversion but "flv to 3gp". I am using Ubuntu 12.04

---

### Post by ranito1980 on 2013-01-12
Have you tried ffmpeg?  I've never used ffmpeg for flv to 3gp conversion but it works great for flv to mp3, mp4 to mp3, etc.

To install ffmpeg:  sudo apt-update && sudo apt-get install ffmpeg

Command for converting files:   ffmpeg -i file.flv newfile.3gp

*Replace the word "file" with the filename of the file (of course).

---

