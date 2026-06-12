---
title: "Need help getting a Philips SPC 1000NC webcam to work in Skype"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by diablo75 on 2010-05-21
I have a system that is running Ubuntu 10.04 that has a Philips SPC 1000NC webcam attached to it.  I've just installed Skype but when I go into it's preferences panel and do a test on the webcam, the feed is just a solid blue screen.

According to this:

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

This cam should be able to work in Linux.  Am I missing something?

---

### Post by no2498 on 2010-05-21
try the cam in cheese webcam booth it should be loaded
look in sound & video


if it does not come on

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1


hope the cam comes on for you

---

### Post by diablo75 on 2010-05-22
Simply installing Cheese did the trick.  Tested it in Cheese, and it worked.  Went back to skype and it then worked.

Thanks for the help!

---

