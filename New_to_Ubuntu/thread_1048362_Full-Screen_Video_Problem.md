---
title: "Full-Screen Video Problem"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by rdmike on 2009-01-23
Hi everyone,

I have a Gateway T-1628 notebook with an ATI x1270 (I believe) controller for the video. After install everything seemed to be going ok as I activated the proprietary ATI driver and have the ATI Catalyst Controller in the Accessories menu. 

Until last night I had only tried a few basic games from the repositories and they worked ok but then I wanted to try out TuxKart, I think it is, and a couple of shooters. That said, video works semi-well unless the game wants to load full-screen. Then all Iget is just a colorful gobbledygook.

I saw another post where it was suggested to run a couple of commands from the terminal which I did.

```
mike@mike-laptop:~$ glxinfo | grep rendering
direct rendering: Yes
mike@mike-laptop:~$ glxgears
301 frames in 5.0 seconds = 60.067 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 49 requests (48 known processed) with 0 events remaining.
mike@mike-laptop:~$ 

```

So, what, if anything, can I do to correct this problem? For what it's worth I was able to run quite a few games on this laptop whith Vista (pre-installed by factory) so I don't think these games are stressing out the video controller. [games example: Knights of the Old Republic, Call of Duty 2, Battlefield 2, and others]

Please let me know if any other information from me is needed to assist in solving the issue and thanks in advance!

---

### Post by rdmike on 2009-01-26
Bump

---

### Post by rdmike on 2009-01-27
I'm still struggling to get this issue resolved. Any suggestions?

---

