---
title: "Logitech QuickCam Communicate STX and Skype on edubuntu v9.10"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by heli2reg on 2010-03-17
Hello Everyone!
 
After researching the forum for quite a bit I am thinking that I may need help from some folks who have dealt with that issue as well.
 
I installed edubuntu v9.10 on my Dell Optiplex GX260. So far so good.
```
uname -a
Linux iXquisite04 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
```
Next came Skype (Beta) version 2.1.0.81.
Then the Logitech QuickCam Communicate STX.
The QuickCam simply would not work.
 
So after researching the forums, I figured that I needed to use the fix described in this thread:
[http://ubuntuforums.org/showthread.php?t=1264689&highlight=Logitech+QuickCam+Communicate+STX](http://ubuntuforums.org/showthread.php?t=1264689&highlight=Logitech+QuickCam+Communicate+STX)
 
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```
With that in place, I can test the QuickCam by using the Test button in the Options menu of Skype.
 
**However, if I am in a call and then activate the QuickCam, at that point Skype will simply close.**
 
**Any idea where to go from here?**
 
Just in case... has that log entry have anything to do with the Skype crash?
> kernel: [ 2459.659938] zc3xx: probe 2wr ov vga 0x0000
 
Thank You for all your help on this!

---

