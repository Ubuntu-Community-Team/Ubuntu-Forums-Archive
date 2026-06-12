---
title: "[SOLVED] Problems opening video files in vlc"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by letters on 2008-12-24
I would like to play avi. mpg.. etc video files. I've installed vlc, but when I try to open a video file. The video and player open for a second and than automatically close down. Anyone know how to fix this problem?

Thank you

:popcorn:

---

### Post by letters on 2008-12-24
???

---

### Post by tomtom1982 on 2008-12-24
Are you using the official version from repositories?

Did you try

```
sudo apt-get update && sudo apt-get --reinstall vlc
```

???

---

### Post by st33med on 2008-12-24
Try not to bump a post within the first 24 hours.  There are people who track down old, unsolved posts.

What version of Ubuntu are you running?  Try doing running vlc in the terminal via:
```
vlc
```
and post what it says when you run one of those files and it crashes.

Also, you probably need to download the codecs for mpeg4 videos. 
```
sudo apt-get install gstreamer0.10-ffmpeg
```

---

### Post by letters on 2008-12-24
> **tomtom1982 said:**
> Are you using the official version from repositories?

Did you try

```
sudo apt-get update && sudo apt-get --reinstall vlc
```

???

I downloaded vlc from [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

---

### Post by tomtom1982 on 2008-12-24
Please use the official repositories and install with synaptic or apt-get.

@ss33med:
> Also, you probably need to download the codecs for mpeg4 videos. 
 
Code:
sudo apt-get install gstreamer0.10-ffmpeg

Vlc doesn't work with gstreamer engine. It has its own ones.

---

### Post by letters on 2008-12-24
> **st33med said:**
> Try not to bump a post within the first 24 hours.  There are people who track down old, unsolved posts.

What version of Ubuntu are you running?  Try doing running vlc in the terminal via:
```
vlc
```
and post what it says when you run one of those files and it crashes.

Also, you probably need to download the codecs for mpeg4 videos. 
```
sudo apt-get install gstreamer0.10-ffmpeg
```

QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

gstreamer0.10-ffmpeg is already installed.

---

### Post by mc4man on 2008-12-24
Try changing video output module.
Open vlc -> tools -> preferences -> click on video and you'll see the 'Output' box. In the drop down move off of default. Try "X11 video output"

Click save

---

### Post by letters on 2008-12-24
> **mc4man said:**
> Try changing video output module.
Open vlc -> tools -> preferences -> click on video and you'll see the 'Output' box. In the drop down move off of default. Try "X11 video output"

Click save

Thank you very much mc4man. Video output is changed and now working!

Thank you everyone for your help.

:KS

---

