---
title: "webcam problem ( trust wb 1400T )"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by mike2507 on 2010-06-02
i think ubuntu does not detect my webcam ( trust wb 1400t )
how can i check/fix this

---

### Post by Guy Sibley on 2010-06-02
What I would first do is look for the make and model of web cam by searching your computer's manufacturer's website. after you have determined this info.  Google Ubuntu drivers for this device.  That has been the easiest solution for my hardware problems in the past.  I hope this is helpful to you.

---

### Post by mike2507 on 2010-06-02
after googling and checking here  [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)
i think my cam is not supported

if somebody has any suggestions , all help is welcome

---

### Post by no2498 on 2010-06-02
most webcams dont need drivers you may need 1 but lets try this first

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

910 and up cheese webcam boothe is/should be installed
look in sound & video
try the cam in cheese


hope this helps

---

### Post by mike2507 on 2010-06-03
perhaps a stupid question , but what kind of program is cheese and where do i find it

nevermind ,i allready found it

---

### Post by mike2507 on 2010-06-04
> **no2498 said:**
> most webcams dont need drivers you may need 1 but lets try this first

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

910 and up cheese webcam boothe is/should be installed
look in sound & video
try the cam in cheese


hope this helps


thanks for the help ( and the others for their sugestions )

---

### Post by no2498 on 2010-06-06
? did it come on

hope it did

---

### Post by mike2507 on 2010-06-11
> **no2498 said:**
> ? did it come on

hope it did

 yes it works after changing some settings in gstreamer

---

### Post by no2498 on 2010-06-13
edit your first post to say solved


glad it helped

---

