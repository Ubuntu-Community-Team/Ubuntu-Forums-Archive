---
title: "how do i find out what webcam i have"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by julianb on 2009-12-22
I bought several EEEpc's. 3 of them (i think) have 0.3megapixel webcams. One is the 10 inch model EEEpc with a better webcam.

I think it's likely I could get a driver kernel module for these things, but I don't know what driver I need. I'm not sure if they work out-of-the-box with Ubuntu but I know they do not work out-of-the-box with TinyCoreLinux, which is my other OS I install on these things. 

Is there a command I can run, to learn what model of webcam these things have, or else a place on the internet that'll tell me? 



The different webcam-equipped machines I have are:
701SD (I have 2)
701 4G (or 700 4G i don't know)
(and, not sure the model of the 10 inch one, don't have it with me)

I am setting these machines up to be used in Haiti for admininstration and fundraising for [Heads Together]("http://facebook.com/headstogetherhaiti")

---

### Post by audiomick on 2009-12-22
How are the cameras connected internally? If it is usb, I think you should see the model with
```
lsusb
```

try it and see.

---

