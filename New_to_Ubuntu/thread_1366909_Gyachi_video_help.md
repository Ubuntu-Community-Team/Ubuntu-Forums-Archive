---
title: "Gyachi video help"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by crowderd on 2009-12-28
Hi there, Im trying to find out how to change gyachi's record preferences from alot of stills to an actuall video format. Im not sure if I need an encoder or some other program. I use Ubuntu 9.10. I am pretty new to ubuntu but am loving every minute of learning about everything so I might need a pretty simple explination. Thank you so much.

---

### Post by FirstByté on 2010-05-24
you are not alone on this wishful wonder. I just wish there's a simpler way of doing it.

Right now, I just dragged and dropped them into a video editor [PiViti] and hope to render them into a video stream. At the moment it's stalling. I'll wait for it though.

---

### Post by FirstByté on 2010-05-24
You might wanna try this out


```
~$ ffmpeg -f **image2** -r img_per_sec -i in00%02d.jpg out.avi
```

Note:
-> that the "-r img_per_sec" specifies how many frame you want to equal one sec.
-> mpg don't really support non-25/29.5 frames / sec, that was why I specified it as ".avi" which and be converted later
-> "%02d" means increment with 2 integer numbers starting from 01. And "%d" will mean increment from 1 - 9.

Check out the link below

> [http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs](http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs)
[http://ffmpeg.org/ffmpeg-doc.html](http://ffmpeg.org/ffmpeg-doc.html)

This helped [worked for] me.

You might give it a try.

---

