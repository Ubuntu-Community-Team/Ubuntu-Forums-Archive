---
title: "ZOOM Display problem"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by Donald1715 on 2010-03-14
My system has an Nvidia video card, which I know has problems with Linux. However, I discovered today that despite the limit of 800X600 when using Ubuntu, by changing the ZOOM setting while on most pages the screen becomes an acceptable size.

PROBLEM:

How to force Ubuntu to stay at a certain Zoom setting? Every time I go to a new web page, I have to Zoom OUT several clicks to be able to see the entire page. Some pages, such as watching a video clip in MSN, has no option to Zoom out and I can only see 1/4 of the page and 1/4 of the video. Any suggestions how to force Zoom to stay put? Or is this a bug in the program?

BTW, Ubuntu is cool and is fun to play with.

Thanks,

D

---

### Post by cariboo on 2010-03-14
Have you got the restricted drivers installed? If you haven't, go to System->Administration->Hardware Drivers and install them. Once the driver has been installed, you can either use the auto resolution, which is on by default, or set the resolution in System->Administration->Nvidia X-Server Settings.

---

### Post by Donald1715 on 2010-03-14
That makes the problem worse. If I update the Nvidia drivers using the driver suggested by Ubuntu, my max display size drops from 800 X 600 to 640 X 480. So it has to be something to do with the ZOOM setting... except I see no way to set an Option for Zoom to stay the same all the time.

In order to see what I'm seeing, if you have a WinXP install, open up IE and go to PAGE, then Zoom and set it to 400%.

---

### Post by J V on 2010-03-14
Did you try editting xOrg.conf and adding a custom res?

---

### Post by Chris Edgell on 2010-03-14
Well, Donald, when I went and looked at your posts I found this thread and knew only too well what you're talking -- I was once stuck in zoom and it looked like 400% for me too.  Finally, can you believe that after always adjusting it manually with Ctrl + or -  ; it actually adjusted itself to an acceptable level and then quite a few months later I installed the Jaunty XUbuntu and it had a much more complex resolution gui "Display" option.

Although I must say, one of my Dells, the other day, snapped to 800x600 resolution and the gui even stopped offering me the 1280x1024 and I was in no mood to work on figuring it out and I just reinstalled.  It did give me pause, just thinking that that kind of quirk could jump out at me anytime.

I wish I knew what J V is talking about; it is the kind of post I like to mark in case it WERE to happen again I'd have a clue about where to start.

---

