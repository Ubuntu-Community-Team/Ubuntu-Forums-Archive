---
title: "Logitech Webcam Woes"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Michael Kaiser on 2009-11-12
Since I'm still an "Absolute Beginner" I figured this was an ok section to post this:

I have an old Logitech m/d V-UD4 Webcam and Karmic Koala. They don't like each other! I had not yet checked my cam's operation since installing 9.10, but last night I installed Skype and checked the cam in the advanced menu. The video box was only green.

Earlier today I installed Cheese and the video worked great. Closed Cheese and tried Skype again. Green. Re-opened Cheese and got the Color Test Pattern. No more video from the Webcam. Removed the cam (it is USB), re-booted, reinstalled, etc. No go.

Can anyone help me here, please?

---

### Post by mcguin on 2009-11-12
Same problem here, there's a workaround that works (at least on my system). Launch from terminal:

$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by Michael Kaiser on 2009-11-12
> **mcguin said:**
> Same problem here, there's a workaround that works (at least on my system). Launch from terminal:

$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Hey, that worked!

Now, do I have to use that command each time I want to use the webcam?

---

### Post by simynona on 2009-11-14
I seem to have the exact same problem with my Gateway laptop's built in webcam, but that solution did not work for me. Instead, after opening Cheese, Skype tells me that it can't find my webcam at all. And then I get the color test pattern from Cheese.

---

### Post by Michael Kaiser on 2009-11-14
> **simynona said:**
> I seem to have the exact same problem with my Gateway laptop's built in webcam, but that solution did not work for me...

Though it did work, the video is painfully slow and distorted. So I really haven't found a solution as of yet. I've had to just put that issue on the back-burner and boot into Windows to use Skype.

---

### Post by Michael Kaiser on 2009-12-01
I never have gotten this figured out.

Here my lsusb info:

Bus 002 Device 002: ID 03f0:4911 Hewlett-Packard PSC 2350
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

It shows the QuickCam, but when I open cheese I see the light on the cam come on for a few seconds as Cheese is loading, then the light goes off and I only see the color pattern with the little box of "snow" in the bottom corner. I have removed Skype in case it was causing some sort of problem.

And help? I sure would be a happier person if I could get this problem solved.

---

