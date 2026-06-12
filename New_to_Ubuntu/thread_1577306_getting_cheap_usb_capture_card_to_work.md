---
title: "getting cheap usb capture card to work"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by markp1989 on 2010-09-18
i brought this last week to record a few tv shows.

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=330467185438&ssPageName=STRK:MEWNX:IT](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=330467185438&ssPageName=STRK:MEWNX:IT)



lsusb shows:Bus 002 Device 003: ID 05e1:0408 Syntek Semiconductor Co., Ltd 


has any one got this working with ubuntu?

Thanks, Mark

---

### Post by davidmohammed on 2010-09-18
very long thread [here]("http://ubuntuforums.org/showthread.php?t=924504&page=13") - work back to front - looks like you can use it, need a bit of effort though.

---

### Post by markp1989 on 2010-09-18
thanks, i have it working.

i can play using vlc like this:

```
cvlc v4l2:///dev/easycap0:width=720:hight=576  :input-slave=oss:///dev/easysnd1 :v4l2-standard=0 

```

but the audio quality sucks :( , any way to sort this out, it sounds high pitched and abit distorted, and keeps breaking up?

also is there any way to record this video? i want to use cron to shows that i keep missing.

Thanks, Mark

---

