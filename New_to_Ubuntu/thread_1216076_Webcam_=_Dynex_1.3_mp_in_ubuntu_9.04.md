---
title: "Webcam = Dynex 1.3 mp in ubuntu 9.04"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by fballem on 2009-07-17
I am trying to get a Dynex 1.3 mp webcam working in ubuntu 9.04. I have attached a screenshot of the output from Cheese. The problem is obvious.

I have run lsusb:

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:0a02 Logitech, Inc. Premium Stereo USB Headset 350
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 4971:ce04  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 19ff:0102 Best Buy 

The Best Buy is the camera - it is a Dynex 1.3 mp.

If there's anything else that I can provide to help diagnose the problem, please let me know.

I have been using ubuntu for about a year, so I'm not a total newbie, but care in providing instructions would be much appreciated.

Many thanks,

---

### Post by earthpigg on 2009-07-17
hi,

have you tried other ubuntu webcam software?

i have found that, for whatever reason, webcams sometimes work flawlessley in one program, but not at all, or crummily, in another.


at the very least, trying a bunch of other ubuntu webcam software packages will let us narrow down the problem.

---

### Post by fballem on 2009-07-18
> **earthpigg said:**
> hi,

have you tried other ubuntu webcam software?

i have found that, for whatever reason, webcams sometimes work flawlessley in one program, but not at all, or crummily, in another.


at the very least, trying a bunch of other ubuntu webcam software packages will let us narrow down the problem.

I tried using luvcview - with the same result. Strangely, I can get video on Skype.

---

### Post by Bagleemo on 2009-08-24
Strange, this same camera works just fine for my system with Cheese. Ubuntu 9.04. Perhaps the libraries have been updated?

---

### Post by fballem on 2009-08-24
I found that if I lowered the resolution, then the camera worked under cheese. I've since changed to karmic for testing, and it seems to have corrected the problem.

That tells me that the drivers have been updated. I don't know if they were updated in Jaunty.

---

### Post by SunnyRabbiera on 2009-08-24
WXcam might solve the issue, I got strange errors with cheese.

---

