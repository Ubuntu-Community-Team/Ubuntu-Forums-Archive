---
title: "libmp3lame"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by thebarisaxkid on 2010-09-25
When I export a video using OpenShot,  I go to file>export and I choose "All Formats", "MP4 (mpeg4)", "DV NSTC", and "High" Quality, but I get an error message saying it could not find the plugins/codecs for libmp3lame.  What is the terminal command line to get/install this plugin/codec, or where can I get the codec in the software center?

Oh btw, I also get an error saying could not find libxvid for MP4(xvid) as well as libx264 for MP4(h.264).  If you can include solutions to these as well, that would be great.

---

### Post by mrhhug on 2010-09-25
try the following
```
sudo aptitude update
```
then
```
sudo aptitude install libmp3lame-dev libmp3lame0 libxvidcore-dev libxvidcore4
```

be sure to post results!

---

### Post by thebarisaxkid on 2010-09-25
Thanks so much! It worked for mpeg4. I havent tried the others, but i'm sure they will work as well!

---

