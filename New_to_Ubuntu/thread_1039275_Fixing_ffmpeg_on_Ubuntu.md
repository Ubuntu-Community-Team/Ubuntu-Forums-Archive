---
title: "Fixing ffmpeg on Ubuntu"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by MooseMagnet on 2009-01-14
Recently evolved from Feisty to Intrepid. I'm stuck trying to get Download Helper to work. I was directed to here:

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

Followed the instructions best I could, but haven't been successful building things. 

Anyone know of simpler way of doing this, or perhaps even a GUI or Synaptics method?

Thanks.

---

### Post by FakeOutdoorsman on 2009-01-14
You can install the **libavcodec-unstripped-51** package in Synaptic.  This will enable some restricted codecs and formats in ffmpeg from the repository.  No compiling needed.  However, if you're feeling adventurous or want the bleeding-edge:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by MooseMagnet on 2009-01-14
Thank you. I found it in Synaptics Pkg Mgr. Now Download Helper works again. I will check out compiling the bleeding-edge.

---

