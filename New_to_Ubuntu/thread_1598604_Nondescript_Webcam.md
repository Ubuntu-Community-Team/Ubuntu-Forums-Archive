---
title: "Nondescript Webcam"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by msmx5s on 2010-10-16
Hi All!

I have a nondescript webcam, bought off ebay (from China) a few years ago... no make, model or drivers...

Any chance of getting it to work in Ubuntu 10.10?

---

### Post by anewguy on 2010-10-16
Maybe.  Does it connect via USB?  If so, plug it in and do the following in a terminal window:

lsusb

Post the output back here and we can go from there.

Dave ;)

---

### Post by msmx5s on 2010-10-16
Thanks anewguy!


Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

That's what it returns :-)

---

### Post by SoFl W on 2010-10-16
Now you have a make and model.

Try [THIS]("http://ubuntuforums.org/showthread.php?t=754916") link.

---

### Post by msmx5s on 2010-10-16
TY both... I'll look into it now and report back :)

---

### Post by cariboo on 2010-10-16
I have one of those, it is detected and works automagically, just install cheese, it's in the repositories.

---

### Post by msmx5s on 2010-10-16
Thanks Cariboo. Cheese works, although I wanted to use it on Skype. Will have to report back later when I get a video call set up! lol

The test video on Skype doesn't work... :-(

---

### Post by anewguy on 2010-10-17
I'm late getting back here, so I'm glad to see it accomplished what I intended anyway.  The "lsusb" command lists all of the USB devices connected to your computer that it recognizes at a hardware level - doesn't mean it will run without a driver.  We needed you to run the lsusb so we could see what vendor/model it was (both from the description itself, but also from the USB identifiers for manufacturer and product, the mmmm:pppp).  With that information I knew we would be able to help you further.  There are a lot of cheap Chineese made cameras out there, so I assumed (not always a good idea!) that it could probably be made to work.

Thanks to everyone who long beat me back to this thread and helped the OP!

Dave ;)

---

