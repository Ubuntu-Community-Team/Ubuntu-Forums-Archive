---
title: "Installing Sound Drivers"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by bigbadbod on 2010-11-25
Hi all,

Am very new to Ubuntu, been a Windows user for years, finally decided to try something else.
I have installed Ubuntu 10.10 and although it works great I have no sound. I have downloaded the driver from the ASUS website, (alsa-1.0.18rc3), but have not got a clue on installing it. I have searched the web and to be frank, I really need a step-by-step idiot guide to install the drivers.
Apologies again, but I am used to Windows.

Best Regards

Bigbadbod

---

### Post by Jeanke on 2010-11-25
Hi,

Can you provide us with the hardware specs of your computer?
Also perform following steps:

Applications --> Accessories --> Terminal

and enter:

```
aplay -l
```

Post the output back.


There are some problems with Asus and sound in Linux.
However some are quite easy to solve (at least it was in my case).

Regards,

---

### Post by bigbadbod on 2010-11-25
Hi, thanks fo the reply. The Ubuntu is on my works PC and am home for the day now. The PC specs are:
 
Asus M4A785TD-V EVO motherboard, (SOCKET AM3),
AMD Phenom 3.0gHz Quadcore.
4GB RAM
 
I ran the 'aplay -l' command earlier today whilst trying to follow another website. After doing what it said, (and going to 3 different sites to ID the results), I think I have a VIA onboard sound card. I will run it again tomorrow and post back.
 
Best Regards
 
Bigbadbod

---

### Post by bigbadbod on 2010-11-26
Hi again Jeanke, I have ran the aplay cmd and get this:

> card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
stephen@Ubuntu:~$ 

---

### Post by Jeanke on 2010-11-26
Hi Bigbadbod,

I'm sorry but I don't have any experience with ATI VIA VT1708S.
I found some posts regarding an Asus motherboard with same sound card:
[http://ubuntuforums.org/showthread.php?t=1204735]("http://ubuntuforums.org/showthread.php?t=1204735")
[http://wwww.ubuntuforums.org/showthread.php?t=1191356]("http://wwww.ubuntuforums.org/showthread.php?t=1191356")

However, these threads are a bit old and also regarding older versions of Ubuntu.
If you are using Ubuntu 10.10 you should have already a more up to date Alsa version as suggested in these posts. Maybe the second part of their solution could help you but I cannot stand for that...

Hopefully some more experienced person will pick up this post and will be able to give you a better and more up to date solution.

Note: I suppose you already checked and played with the sound settings under System --> Preferences --> Sound right?

---

### Post by bigbadbod on 2010-11-26
Aye, I have played with the sound settings but the speaker icon stays red with 2 horizontal lines coming out of it.
Thanks for your help anyway.
Might as well un-install and stick with Windows.
The great experiment failed lol
 
Best Regards
 
Bigbadbod

---

### Post by bigbadbod on 2010-11-26
:oops: Errmmm.........I have been a complete idiot, just booted Ubuntu up for one last play around before un-installing and played with the sound settings. I just noticed the 'mute' button was on :confused:. Now I have not pressed that, for some reason it has installed muted unless I have installed the sound driver by accident.

So that means I will be on here a lot more asking stupid questions.

Thanks again Jeanke, you sort of fixed it lol

Best Regards

Bigbadbod

---

### Post by Jeanke on 2010-11-26
:D Loll alright, such things happen to all of us from time to time...
Glad you found it!
Besides no questions are stupid! So no worries ;)

Can you mark this thread as solved?
You can do this by going to "Thread Tools" (on top of the page) and select "Mark as solved".

Cheers

---

