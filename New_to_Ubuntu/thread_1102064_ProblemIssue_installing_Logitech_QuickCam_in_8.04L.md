---
title: "Problem/Issue installing Logitech QuickCam in 8.04LTS"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-21
Ubunteros,

I recently completed a fresh 8.04 install. Now I would like to install the Logitech QuickCam model 961462-0403 for use with Skype.

I have another PC running 8.04 and it uses the exact same model webcam. When I installed it everything was plug and play and Skype worked perfectly.

However, on this new machine Skype doesn't even show the video. So I'm lost as to what is wrong! I will add that I did add the SABRENT Philips saa7130 TV turner card. This was installed first. Maybe that screwed up some ordering?

Any help to resolve this matter is appreciated. Thank You!

---

### Post by suomalainen on 2009-03-21
Ubunteros,

I don't know if this info helps but here is the output from lsusb.

I would like to note that I installed my tv turner first. I have also noticed the following:

When I open "tv time" I can see the different tv channels. THEN when I open skype and go to Options>Video Devices>Test THEN I can see my video BUT I can't call out because SKYPE reports "Problem with Audio Playback"

help would be appreciated.



Terminal output from lsusb

george@george-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08af Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by suomalainen on 2009-03-21
Ubunteros,

I got the audio issued resolved by doing the following:

OPTIONS---> SOUND DEVICES

For Sound In I set it on VIA 8237 (hw:V8237,1)
And Sound Out VIA 8237 (hw:V8237,1)

Ringing = Default device (default)

Under, VIDEO DEVICES I noticed that my TV Turner is:
Sabrent SBT-TVFM (saa7130)(/dev/video0)

Is there something here that is affecting my being able to see live streaming of myself when in a Skype call????

---

### Post by suomalainen on 2009-03-21
echo.....

---

### Post by diablo75 on 2009-03-22
You might check this out:

[http://davestechsupport.com/blog/2009/02/14/installing-webcams-in-ubuntu-the-easy-way/](http://davestechsupport.com/blog/2009/02/14/installing-webcams-in-ubuntu-the-easy-way/)

I can't promise you it will work, but chances are good that it will do the trick.

---

### Post by suomalainen on 2009-03-22
diablo75,

Thanks for the info! I gave it a try but it didn't work. I really don't think my issue is a driver related one. As mentioned above, I can see my Skype video but only when I first launch TVTIME and then launch Skype.

As noted above, it kinda appears that TVTIME needs to take control of the TV turner first before the webcam can be taken into use by Skype, if that makes sense.

Anyone out there know what I can do?????

P.S. the instructions to the blog you noted, as per the install, were well written!

---

