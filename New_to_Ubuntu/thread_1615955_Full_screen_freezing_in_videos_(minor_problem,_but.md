---
title: "Full screen freezing in videos (minor problem, but annoying)"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Dr Heelhook on 2010-11-07
I keep posting threads in the Abs. Beg. forum, because I'm not knowledgable enough to determine the difference between a typical beginners problem and a more complicated problem, but here we go:

Whenever I watch videos in certain websites, like youtube and megavideo, almost every time I try to watch in full screen, the screen just freezes on the frame. The sound works properly, but the picture freezes. It does this almost every time I click the full screen icon and in order to be able to watch, I need to got to full screen and if it doesn't work, I need to go back to normal screen and to full screen again, back to normal, then to full again until the picture starts moving. Sometimes it works after a few tries and sometimes you can do the procedure like 10 times and the screen keeps freezing up. This started after I installed Ubuntu, that's why I'm asking here. Has anyone else had this problem and if so, is there some way in which you can fix it for good?

Thanks
/Oskar

---

### Post by bioterror on 2010-11-07
Which browser are you using? I'm running Chromium and I didnt notice nothing more than a little freezing when moving to full screen mode. If you're using FireFox, try Chromium, if you're using chromium, then vice versa or something...

ps. you made me to watch katy perry video :lol:

---

### Post by Autodave on 2010-11-07
> **Dr Heelhook said:**
> I keep posting threads in the Abs. Beg. forum, because I'm not knowledgable enough to determine the difference between a typical beginners problem and a more complicated problem, but here we go:

Whenever I watch videos in certain websites, like youtube and megavideo, almost every time I try to watch in full screen, the screen just freezes on the frame. The sound works properly, but the picture freezes. It does this almost every time I click the full screen icon and in order to be able to watch, I need to got to full screen and if it doesn't work, I need to go back to normal screen and to full screen again, back to normal, then to full again until the picture starts moving. Sometimes it works after a few tries and sometimes you can do the procedure like 10 times and the screen keeps freezing up. This started after I installed Ubuntu, that's why I'm asking here. Has anyone else had this problem and if so, is there some way in which you can fix it for good?

Thanks
/Oskar

Gimme a minute....I just found the solution to that problem last night and it fixed both of my machines with that problem.......I'll find it and post it.

---

### Post by Autodave on 2010-11-07
Whenever I watch videos in certain websites, like youtube and megavideo, almost every time I try to watch in full screen, the screen just freezes on the frame. The sound works properly, but the picture freezes. It does this almost every time I click the full screen icon and in order to be able to watch, I need to got to full screen and if it doesn't work, I need to go back to normal screen and to full screen again, back to normal, then to full again until the picture starts moving. Sometimes it works after a few tries and sometimes you can do the procedure like 10 times and the screen keeps freezing up. This started after I installed Ubuntu, that's why I'm asking here. Has anyone else had this problem and if so, is there some way in which you can fix it for good?

Thanks
/Oskar[/QUOTE]

I still had it on my thumb drive.....I did NOT come up with this....someone else did and I am sorry that I can't give them credit for it, but here goes.  Open a terminal and type this in:

sudo mkdir /etc/adobe
sudo su
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

That should fix your problem.

---

### Post by Dr Heelhook on 2010-11-07
> **Autodave said:**
> 

I still had it on my thumb drive.....I did NOT come up with  this....someone else did and I am sorry that I can't give them credit  for it, but here goes.  Open a terminal and type this in:

sudo mkdir /etc/adobe
sudo su
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

That should fix your problem.
Wow, that's quick work. It seems to be working now. Thanks a lot.

---

