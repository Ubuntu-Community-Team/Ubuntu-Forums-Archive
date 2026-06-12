---
title: "audio/video issues"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by ticky on 2010-12-15
Hi...very new to ubuntu and linux. I just switched over. I have a dell 4550. I am having some problems playing audio and video files...including flash video.  Not sure if this is a driver problem maybe?

---

### Post by daqron on 2010-12-16
Congratulations on switching over!

I imagine you'll want to post some more detail here before anyone can really help answer your question. What happens when you try to play audio/flash? Do you get errors? Does it sound weird? Does it seem to play but you don't hear anything (i.e., possible driver issue)?

Without knowing the nature of your problems I'll just suggest going to the Ubuntu Software Center (under the Applications menu) and installing Flash Player and "ubuntu-restricted-extras" (for mp3 and other audio files).  

Usually if you post enough detail here in the forum you'll find lots of smart people who can help out.

---

### Post by karthick87 on 2010-12-16
Have you installed all the codecs???
```
sudo apt-get install ubuntu-restricted-extras
```

Installing this package will have support for playing MP3 files to decode other audio formats (with the addition of GStreamer).

---

