---
title: "Lost webcam with recent update"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by mangurt on 2009-12-10
Greeting all,
I have a Dell inspiron 1525 running ubuntu 9.10.  I have an intergrated webcam that works (I used it last night).  I went to skype with my wife today, and it said that I did not have a webcam.  I fired up Cheese, and Cheese said that I do not have a webcam either.  Typing ls /dev/vid* results with no such folder.
Any help would be greatly appreciated.
Thanks

---

### Post by gordintoronto on 2009-12-10
If you start a terminal and enter lsusb does the webcam show up?

Is there any chance that a cable came loose?  Maybe inside the case...

---

### Post by mangurt on 2009-12-10
The webcam is not an external webcam.  I ended up going back to the .15 kernal and things are working.  I don't know what the kernal did to it.

---

