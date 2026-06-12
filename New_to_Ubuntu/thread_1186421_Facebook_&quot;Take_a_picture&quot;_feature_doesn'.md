---
title: "Facebook &quot;Take a picture&quot; feature doesn't work with Ubuntu."
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-13
So on facebook, you can take a picture directly from webcam.

It doesn't work in Ubuntu however because it doesn't detect the camera or something...

Any ideas?

---

### Post by PureLoneWolf on 2009-06-13
We would need to know the make/model of the webcam and also the output of typing lsusb into a terminal.

---

### Post by donkyhotay on 2009-06-13
Also can you take a picture with the webcam outside of facebook with another program?

---

### Post by Gp. on 2009-06-14
I can use cheese to take a picture.

Here's the output
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 004: ID 046d:c714 Logitech, Inc. 
Bus 006 Device 003: ID 046d:c713 Logitech, Inc. 
Bus 006 Device 002: ID 046d:0b04 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 04f9:0033 Brother Industries, Ltd 
Bus 005 Device 002: ID 046d:c048 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Sub101 on 2009-06-14
I do not think it is a Make/Model issue.

My webcam works fine but will not work with the facebook feature.

---

### Post by Gp. on 2009-06-14
It doesn't know how to communicate with Ubuntu...

---

### Post by Gp. on 2009-06-21
It's because Flash doesn't work with Webcams and such on Ubuntu, anyone know how to get it working with flash?

---

### Post by edd07 on 2009-06-21
> **Gp. said:**
> It's because Flash doesn't work with Webcams and such on Ubuntu, anyone know how to get it working with flash?
Buying Adobe and opening Flash up, I guess. :P

---

### Post by jamieh on 2009-06-21
The easiest solution would be for someone to prepose a law banning proprietary software, but we all know that ain't gonna happen.

---

### Post by tedtlogan on 2009-08-29
This is how you access it:

[http://www.facebook.com/swf/coney_island.swf?8:151838:1](http://www.facebook.com/swf/coney_island.swf?8:151838:1)

then click allow/remember.

---

### Post by olivierp on 2009-09-29
> **tedtlogan said:**
> This is how you access it:

[http://www.facebook.com/swf/coney_island.swf?8:151838:1](http://www.facebook.com/swf/coney_island.swf?8:151838:1)

then click allow/remember.

Excellent link, thanks alot !

---

### Post by FrankyG on 2010-05-19
Also, you can manage your flash settings for video and audio etc. here:
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html)

---

### Post by FrankyG on 2010-05-19
Also, you can manage your flash settings for video and audio etc. here:
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html)

---

### Post by kubuntero on 2010-11-30
> **tedtlogan said:**
> This is how you access it:

[http://www.facebook.com/swf/coney_island.swf?8:151838:1](http://www.facebook.com/swf/coney_island.swf?8:151838:1)

then click allow/remember.

thanks! that works!

---

### Post by no2498 on 2010-12-01
make sure you set the sites you use
this is how some one else can start your cam
just a heads up

---

### Post by bornagainpenguin on 2011-01-28
> **tedtlogan said:**
> This is how you access it:

[http://www.facebook.com/swf/coney_island.swf?8:151838:1](http://www.facebook.com/swf/coney_island.swf?8:151838:1)

then click allow/remember.

Thank you for this!  I couldn't figure out why I was having problems when cheese was seeing things just fine!

--bornagainpenguin

---

### Post by gewone on 2011-04-03
Thanks a lot for this thread. However, when I visit that link through Firefox (latest 4.0) I don't get that Flash popup box where I can choose to allow the site to reach out for cam/microphone or not. Simply nothing. Also tried visiting Flash settings at adobe.com, but clicking "Always ask" won't do a thing. There's no "Apply" button but I can just click 'Confirm' and then I'm back on the config applet (which it says is v3.23, for that matter). Aawergh, any ideas?

---

### Post by no2498 on 2011-04-04
at/on the adobe site in the settings manager you set it to allow and remember
the settings manager does not come up on all sites
visit the site you use then go to adobe
that way the site is in the list

---

