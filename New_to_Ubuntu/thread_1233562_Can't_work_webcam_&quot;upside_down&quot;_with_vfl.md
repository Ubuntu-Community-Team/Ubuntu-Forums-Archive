---
title: "Can't work webcam &quot;upside down&quot; with vflip"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by jgratero on 2009-08-06
I've have a messenger 310 Genius webcam that I've been trying with Xubuntu, and so far, these are my issues:

-The image is upside-down
-can't use camorama with it (error "unable to capture image")

I've tried this procedure:

> cd /sys/class/video4linux/video0
echo 1 > vflip
cat vflip 
1 And all I get is this:

> bash: vflip: *No such file or directory*

Is this a UVC video related issue?

---

### Post by m4n_in_bl4ck on 2010-04-06
Have you been able to find a solution for this? I have the exact same webcam model and the exact same problem (image appears upside down). :S

---

### Post by Mykk on 2010-04-06
Turn the webcam upside down, if it wont stay in place - use blue tack ;)

---

