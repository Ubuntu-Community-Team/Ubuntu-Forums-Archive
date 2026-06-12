---
title: "Hue Hd webcam problem"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by biba82 on 2010-01-07
Hi everyone,

For Christmas, I bought my girlfriend a Hue HD Webcam. Yesterday I wanted to install it on her Ubuntu 9.10. However, it did not want to work, after putting aside the useless installation CD, I googled and found following link:
[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

Now comes the part where I have to reveal my utter inability to work with Ubuntu (at least so far ;))

I think I didn't get any further than Step "4. Building Microdia driver from source"
By that I mean that I am not sure if I downloaded the microdia kernel driver source.
Okay,

'$ cd microdia
$ make'

and that was no obvious problem. But in Step 5, I came across following problem.

After command:

'# insmod ./sn9c20x.ko'


I get this message: 

'insmod: error inserting './sn9c20x.ko': -1 File exists'


In the troubleshooting guide, there is a solution, and that's where I am totally stuck...

After following command:


'$ lsmod | grep sn9c20x'


I get this response:

'sn9c20x                72816  0 
videodev               36736  2 sn9c20x,uvcvideo'


This is where I have to quit, I just don't know what to do ....

Please help me!

Cheers!

---

### Post by no2498 on 2010-01-08
you need a program to open an see the cam with
try a few diff 1's lick cheese, wxcan, xawtv
you can open terminal type ( gstreamer-properties )
click video try v4l1 or v4l2 
if it comes on good if not try something else

---

### Post by smythe on 2010-01-14
if yours is one of the current hue cams they are uvc, so you probably just need to check your gf's uvc installation  [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

---

