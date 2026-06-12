---
title: "Cheese question"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by e.jejcic on 2010-04-16
Good nigh to everydy:
I just installed Cheese in Ubuntu 9.04.m When I open cheese there is no image from webcam and the lights of camera never closes,I have to shut down Ubuntu..I am really a noob. What"s wrong, I don"t know what to do. .I need help. Thank"s from Eduardo.

---

### Post by Sef on 2010-04-17
How did you install cheese?

---

### Post by MichealH on 2010-04-17
Did you install it by ```
sudo apt-get install cheese
```?

If not try this [link ]("apt://cheese")(Installs it automatic APTURL link)

---

### Post by e.jejcic on 2010-04-17
Good afternoon:
I installed withm add/remove programs. Then I remove and installed it with the same mechanism 2-3 times with same result. Just now I installed again with sudo in terminal and still same problem. I realized that it takes almost 1 minute to load. It then goes to a screen showing several colors vertical stripes and at bottom of screen shows 3 squares of diferent colors and the last one looks as the TV sacreen when there is no signal (?) Then I press "effects" and shows different graphics.
I was thinking if I need some kind of driver for thi stupid chinese camera.
Anyway, with sudo installation when I close Cheese it still leave the lights of the camera on. I hope did myself clear enough. Thanks again from Eduardo.

---

### Post by no2498 on 2010-04-17
this will help see your cam

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

you may need to do this over if cheese does not see the cam

if after a few trys get a diff cam program

---

### Post by e.jejcic on 2010-04-17
Good night:
I did all you suggested. All is the same. Now, how i get a different camera program?. Thanks from Eduardo.

---

### Post by e.jejcic on 2010-04-19
Bump.

---

### Post by no2498 on 2010-04-20
getdeb also has this 1 wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

did the cam come on in the gstreamer-properties

if it did not come on programs will not help

you may need to load the lib v4l so

to make the cam work

---

### Post by Jbike on 2010-04-24
All the sudden Cheese no longer works for me? I tried then to start cheese from a terminal, then from a root terminal, both times I received the following response:

root@jbike-desktop:/home/jbike# cheese
Error re-scanning registry , child terminated by signal


My 9.10 system is fully up to date. Anyone have any idea what broke Cheese? I also recently installed Lives, but I don't think that would have broken cheese would it? 

Thanks, Jbike

---

### Post by no2498 on 2010-04-24
Jbike if cheese was working and broke the cam

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

i myself like this program wxcam
read and install all the page tells you to
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

and do not open cheese

---

### Post by Jbike on 2010-04-24
splicerr solved this in another post of mine, PiTiVi, broken. Here is the answer to both problems:


[https://bugs.launchpad.net/ubuntu/+s...vl/+bug/456530](https://bugs.launchpad.net/ubuntu/+s...vl/+bug/456530)

Thanks for your reply, and I hope this helps others too. 
Jbike

---

