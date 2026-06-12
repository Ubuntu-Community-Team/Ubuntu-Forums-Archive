---
title: "Xorg-intel whitescreen freeze problems..."
date: 2009-10-25
forum: New to Ubuntu
---

### Post by 11010110 on 2009-10-25
Hey all,

I was attempting to find a way to stabilize flash video output by trying different xorg-intel drivers. I had been running 2.4 for about 4 months because it was creating flawless performance but last month all of that changed for an unknown reason (something in one of the upgrades I guess). I tried going with the current driver which disabled fullscreen so then I went with the 2.8 preview driver. Upon restarting after installing 2.8 the computer would start normally yet freeze about 10 seconds after the desktop appeared. I started up a new session into a root terminal and rolled back into the current driver and then back to 2.4. Now when the computer starts the screen becomes completely white (yet the mouse retains full functionality). I can suspend my session via the keyboard and the normal login screen appears and then goes to white once logged in. This leads me to think it is X related but I have no idea where to go from here. I am running my Vista backup until I get it back lol so I hope I can get up and running soon! 

Thanks to all in advance sorry for the wordy post.

---

### Post by 11010110 on 2009-10-25
Hey again,

I managed to fix it by using a combination of different drivers (installed in root shell because X was still unavailable) and I also used fix x and other tools in the safe mode startup section. I don't know what exactly worked because I just kept cracking away at it. But something worked! Then I switched to the Opera browser (flash works MUCH better in Opera vs FF).

---

### Post by hackerlife on 2009-11-07
Hey, would ya mind going through the steps you took?
I seem to have the same problem

I disabled my driver, restarted, and get a white screen after I log in (but, funnily enough, a fully functional desktop. I can actually click "Shut Down" blind! lol)

Thanks for any and all help

---

### Post by 11010110 on 2009-11-09
Hey,

Im not quite sure what exactly worked for me. I just switched back and forth between the current xorg-intel driver and the 2.4. 

```
sudo apt-get install xserver-xorg-video-intel-2.4
```

and

```
sudo apt-get install xserver-xorg-video-intel
```

It just started working for me lol. Sorry I can't be of more help. Since then I have upgraded to Karmic and all of the intel driver problems have beeen fixed (for the most part). If you are up for it and the drivers don't work you could always try goin to karmic.

Good luck!

---

