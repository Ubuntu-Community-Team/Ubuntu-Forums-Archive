---
title: "mplex"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by grammarian on 2010-05-15
Hi Everyone,

I'm trying to burn a DVD video using Brasero however when I hit the burn button, I get a message telling me that I need mplex to continue. I've installed mjpegtools, etc but the message continues to appear. Is there any way I would be able to download mplex to get my movie to burn?

Thanks in advance for your help!!!

Regards,

---

### Post by jamesa00789 on 2010-06-11
I am also having this problem. Bump.

---

### Post by labinnsw on 2010-06-12
[Solution: 4th answer in this thread.]("https://answers.launchpad.net/ubuntu/+source/brasero/+question/112041")

---

### Post by whitemagicwoman on 2010-09-12
I'm having this problem too.

So, reply four on that thread says the following:

"From: [https://lists.ubuntu.com/archives/ubuntu-burning/2009-January/007212.html](https://lists.ubuntu.com/archives/ubuntu-burning/2009-January/007212.html)
 You need to install: "gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad-multiverse and libavcodec-unstripped-52"
 Also install dvdauthor."


I installed dvdauthor using the Ubuntu Software Center.  I tried to install libavecodec-unstripped-52 from the Medibuntu package site but nothing seems to be happening when I click "click to install."  I'm not sure how to do the rest.  



Can anyone give a few more detailed suggestions for us absolute beginners?

---

### Post by whitemagicwoman on 2010-09-12
I found a fix here: [http://ubuntuforums.org/archive/index.php/t-1523005.html](http://ubuntuforums.org/archive/index.php/t-1523005.html)

The first response worked for me, which was to enter the following in a terminal:

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```

:D

---

