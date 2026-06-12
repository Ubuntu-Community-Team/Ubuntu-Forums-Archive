---
title: "S-Video Output Resolution"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by SubOne on 2009-01-09
After trying many different configurations for xorg.conf, that I found on various pages on the web, and failing at getting s-video to work without forcing X to load into low res mode on reboot, I finally reinstalled the ATI restricted driver and took the following action proposed by someone in #ubuntu:

```
sudo aticonfig --initial
sudo aticonfig --ovt=disable
```

This seems to have worked for enabling the S-Video output to my television. However, now the resolution of the image on the television is larger than the TV allows. The television shows a clone of my desktop on my laptop screen at 1680x1050, but only shows 1024x768 of it and shows the other parts when I move the mouse to that edge of the screen.

My question is: How do I set the resolution for the TV image so that it is the full size of the TV and not scroll when the mouse moves to the edge? Preferably this will be a separate view than the laptop's screen at 1024x768 (or perhaps something more appropriate 800x600? 640x480?) so that I can full screen a video onto the TV screen.

---

### Post by wizard10000 on 2009-01-09
Hiya, SubOne -

Unfortunately an s-video port isn't designed to do anything close to 1680x1050 so I think another view is the only way to do it.  I run single monitors here and have no recent experience with ATI cards and Linux so I'm gonna back out at this point  ;)

---

### Post by SubOne on 2009-01-12
Yes I am aware that the TV cannot display 1680x1050, I thought I made my self clear that I wanted it to display 1024x768 on the TV.

---

### Post by insane_alien on 2009-01-12
S-video can't do that either 576i(PAL) is going to be the highest resolution you can output. 

your looking at 720 by 576 whether you like it or not, alternatively, you can go for the lower resolution NTSC format.

---

