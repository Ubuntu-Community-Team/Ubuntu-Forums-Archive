---
title: "no sound on a clean install"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by Garthhh on 2010-07-03
I'm on a gateway 7330gz notebook
Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97  Audio Controller
       vendor: Intel Corporation


also joined this bug report
[https://answers.launchpad.net/ubuntu/+question/44916](https://answers.launchpad.net/ubuntu/+question/44916)

the choices are no longer recognizable to me here in july of 2010, running ubuntu 10.04 lts & or mint 9
I can open up sound preferences & select one of these choices:
off
analog stereo input
digital stereo duplex IEC 958
digital stereo output [IEC 958] + analog stereo input
analog stereo output
analog stereo duplex

I tried them all, no joy
went to alsamixer
& can find the external setting, but can't make it change states
went to lord raiden's comprehensive sound problem guide
[http://ubuntuforums.org/showthread.php?t=205449&page=24](http://ubuntuforums.org/showthread.php?t=205449&page=24)
went to the alsa project page & there is no driver for this particular sound card...
ran this in terminal
 ~ $ grep 'audio' /etc/group
[noparse]audio:x:29:pulse[/noparse]

the interesting thing is I had sound on mint until I did a clean install, I don't know exactly how I got it working , but I was using the same resources.
This time I'm documenting as I go...
Thank you

---

### Post by Garthhh on 2010-07-04
bump

---

### Post by Garthhh on 2010-07-05
bump

---

### Post by Garthhh on 2010-07-06
I went here
[http://wiki.ubuntuforums.org/showpost.php?p=9444100&postcount=1781](http://wiki.ubuntuforums.org/showpost.php?p=9444100&postcount=1781)
& went to sound preferences/hardware tab
Changed to analog stereo output
output tab/connector
Analog output, no amplifier

---

