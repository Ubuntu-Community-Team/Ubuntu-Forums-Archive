---
title: "Is there a difference between shutting down via command line vs GUI button?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by BassKozz on 2009-02-02
Is there a difference between shutting down via the GUI (top-right shutdown button) vs. command line 'shutdown -h now' ?
I am just curious if shutting down in terminal might be a different sort of (more abrupt) shutdown or is it all the same?
TiA,
-BassKozz

---

### Post by SunnyRabbiera on 2009-02-02
> **BassKozz said:**
> Is there a difference between shutting down via the GUI (top-right shutdown button) vs. command line 'shutdown -h now' ?
I am just curious if shutting down in terminal might be a different sort of (more abrupt) shutdown or is it all the same?
TiA,
-BassKozz

should all be the same

---

### Post by Crafty Kisses on 2009-02-02
Honestly, I don't think so.

---

### Post by 7mkgw7q on 2009-02-02
I am not aware of any difference. I believe it is just a GUI vs non-GUI method.

---

### Post by Gotaro on 2009-02-03
There must be a difference, because the GUI shutdown hangs for me, but the command line method works.  For you guys who said it was the same, here's the thread about my problem:
[http://ubuntuforums.org/showthread.php?t=1058234](http://ubuntuforums.org/showthread.php?t=1058234)

I can't logout without it hanging, either, which makes me think maybe there's a separate logout process for the GUI method or something..  I'm using KDE 4.2.

---

### Post by BassKozz on 2009-02-06
yes/no/maybe so

---

### Post by SteveNorman on 2009-02-06
guis use more system resources,,command line is closer to the 1's and 0's.

---

### Post by chrisod on 2009-02-06
I have a similar issue with standby. It crashes with the GUI, works just fine from the command line. So I'm in the "there is a difference" camp.

---

### Post by avtolle on 2009-02-06
I suspect that the problem lies not within the shutdown or suspend processes themselves, but rather with the GUI front-end. To explain, the basic processes are the same whether executed from the command line or from the GUI; but, in order to work correctly from the GUI, the GUI needs to not hang or otherwise interrupt the sending the correct command to the system. Thus, the "hang" or "crash" mentioned by some posters relate to issues with handling the GUI by the system, and not with the processes themselves. Thus, there is no difference, as the processes are the same; the difference lies within the use of the different method of activating the process. The different results given above demonstrate that; the command line works with no problems, use of the GUI results in a hang or a crash.  So, to resolve, one must determine what the problem is with the GUI, and for that, I have no idea, but suggest to the poster who had to disable DRI for the video card to work that this might be one potential explanation of the difference observed.

---

### Post by chrisod on 2009-02-07
Oddly, my system suspends just fine from the GUI. It won't come back up though. I have to do a hard reboot.  If I suspend from the command line and close my lid, it comes up perfectly when I open the lid again.

---

### Post by Gotaro on 2009-02-07
> **avtolle said:**
> I suspect that the problem lies not within the shutdown or suspend processes themselves, but rather with the GUI front-end. To explain, the basic processes are the same whether executed from the command line or from the GUI; but, in order to work correctly from the GUI, the GUI needs to not hang or otherwise interrupt the sending the correct command to the system. Thus, the "hang" or "crash" mentioned by some posters relate to issues with handling the GUI by the system, and not with the processes themselves. Thus, there is no difference, as the processes are the same; the difference lies within the use of the different method of activating the process. The different results given above demonstrate that; the command line works with no problems, use of the GUI results in a hang or a crash.  So, to resolve, one must determine what the problem is with the GUI, and for that, I have no idea, but suggest to the poster who had to disable DRI for the video card to work that this might be one potential explanation of the difference observed.
I fail to see how this poster proved that there really isn't a difference.  It seems he just confirms that there is one, but takes a tone like he is proving otherwise. ;)

Bottom line: YES, there is a difference.  If anyone can help me fix my GUI shutdown, please let me know!

---

### Post by chrisod on 2009-02-08
If it works from the command line just do it that way and go on with your life. Driver issues (if that the issue) are tremendously difficult to pinpoint, and if you have an alternative way of shutting down safely, it's really not worth the effort of going down that rabbit hole. There is always a chance the problem will resolve itself with 9.04.

---

