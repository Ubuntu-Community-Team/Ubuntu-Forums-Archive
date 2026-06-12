---
title: "Acer Aspire 2920Z - Crystal Eye - XSane Image Scanner"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by raedq on 2008-12-21
Hi All...

I have installed Ubuntu 8.10 and it is all sweet and nice... One thing though is that when i want to grab a picture using my Crystal Eye Acer-Aspire embedded camera using XSane i get this message:

Failed to open device: 'v4l:/dev/video0':
Invalid argument

Using Ekiga, i know my camera works using v4l2 (if that makes sense) but I can't get it to work on XSane or any other graphics application.

Appreciate your help

---

### Post by gn2 on 2008-12-21
Have you tried [Cheese]("http://projects.gnome.org/cheese/")?

You can install it through Add/Remove, Synaptic or a good old fashioned ```
sudo apt-get install cheese
```

After installation it can be found in Applications > Graphics

---

### Post by darkwalt on 2008-12-22
Ok, somewhat same question.  I can use the camera using luvcview, but not cheese.

---

### Post by scohar70 on 2008-12-22
I have similar problems with my Dell Studio 15 (model 1537) webcam.  After much searching on the Internet and the forms, I pretty much see that it doesn't work with v4l, but does work with v4l2. 

If I open /dev/video0 with v4l2 using vlc, it works!  I can see myself!

So far, I cannot find any data that shows that sane supports v4l2.  I've tried enabling it, but can't get it to work. 

Does anybody know how to get sane to recognize v4l2?

---

### Post by scohar70 on 2008-12-22
Incidentally, xawtv seems to support v4l2 and works OK.

Cheese does not work.

---

### Post by darkwalt on 2008-12-24
> **darkwalt said:**
> Ok, somewhat same question.  I can use the camera using luvcview, but not cheese.

Ok, video capture works via vlc, but still not via cheese.

---

### Post by raedq on 2008-12-24
> **scohar70 said:**
> Incidentally, xawtv seems to support v4l2 and works OK.

Cheese does not work.

xawtv worked fine thanks !!! so there is no hope for xSane?:(

---

### Post by pizpot on 2009-01-29
My Aspire 5920 crystal eye worked fine in 8.04 and cheese. Now in 8.10, in cheese, I must drop the resolution down to160x120 for it to work.

---

