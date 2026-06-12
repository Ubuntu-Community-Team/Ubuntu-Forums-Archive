---
title: "Webcam not working in Skype"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by suomalainen on 2010-03-17
Ubunteros,


My webcam under 8.04LTS worked just fine. Now when I use it for Skype in 9.10 nothing happens.

What should I be doing to get it to work?


Thank You!!!

---

### Post by suomalainen on 2010-03-17
Hello Again,

I swapped out webcams to see if that makes a difference. This time I'm using a 3COM Model 0776. As you can see from the attached pic as soon as I click on "TEST" Skype crashes and closes itself.

The other webcam I got is a Logitech QuickCam Chat. This too failed in Skype.

---

### Post by heli2reg on 2010-03-18
Hello,
 
Not sure if you have seens my earlier post from today [http://ubuntuforums.org/showthread.php?t=1432195](http://ubuntuforums.org/showthread.php?t=1432195)
 
I have not tested the Logitech QuickCam Communicate STX with an earlier version of Ubuntu so I do not have a whole lot of experience. It seems as if Skype itself may have issues, though.
 
Just wondering: Have you tested your web cam with "cheese" yet as suggested here [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) ? I am just about ready to do that on my Edubuntu v9.10 machine, which as far as I understand is pretty much the same as your Ubuntu v9.10 with the exceptions of some preloaded educational software (that I have launched my 3-yr old against today).
 
Can you please specify your complete Skype version? - I am running v2.1.0.81 and do not have access to an earlier version. I would very much like to test an earlier version of Skype on Ubuntu v9.10.
 
Further, the interesting thing is that I can get my QuickCam Communicate STX just work fine for the "Test" button under the "Options" menu. Everything seems working fine there. Also, I have made a call for quite some time using the QuickCam's mic. That seems to work fine as well.
However, Skype will simply close once I activate the video during an ongoing call. At that point Skype closes and the call hangs up.
 
I will do some testing with the QuickCam using "cheese" or some of the other apps suggested as part of the guide (provided in the link above) next and see how that goes.
 
If anybody could provide a download link for an older version of Skype, I would very much appreciate that. It may simply be a recent change within Skype causing it to crash with the Logitech QuickCam Communicate STX.
 
Thanks!

---

### Post by mastablasta on 2010-03-18
double post, please delete.

---

### Post by mastablasta on 2010-03-18
I downloaded Skype deb file from Skype.com and then installed it (i somewhere read that the one in repos has an issue). then i used the fix described above (sort of). I created a script (with a help from IRC Ubuntu community member) so i dont' have to constantly type this in terminal
 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
 
which i think is similar to the post above.
 
now it just works.
 
note my camera also worked in cheese before and also with that gstreamer properties command and then test, just not in Skype. It was also propperly recognised by linux.

---

### Post by prj44 on 2010-03-20
Creative Live Ultra won't work on 9.1.

Shows properly in report of what is connected to the USB.

Does not show up in Cheese or Skype.

Camera is known good.

Instructions on getting a webcam to work are confusing.  

Any ideas most welcome.

---

