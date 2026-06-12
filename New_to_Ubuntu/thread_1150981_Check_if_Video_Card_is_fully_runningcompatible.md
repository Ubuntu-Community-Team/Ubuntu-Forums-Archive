---
title: "Check if Video Card is fully running/compatible?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-05-06
This maybe an easy question to answer.

How do I know if my ATI Radeon 7500 laptop card is running to it's full potential. I know there are compatibility/driver issues with a lot of cards with linux so I'm not sure if mine is okay.

Is there a command to print out some sort of report??? And how would I interpret the results?

---

### Post by RedSingularity on 2009-05-06
One easy way to see if its running is if you can enable desktop effects.

---

### Post by Hospadar on 2009-05-06
I would say the only thing that really matters is if it's working to your satisfaction.  It's very hard to determine how well exactly the video card is performing (especially as to whether or not there are video errors, etc) without looking at the real output.

If you feel like things should be going faster, you could try the restricted drivers System->Administration->Hardware Drivers

---

### Post by LowSky on 2009-05-06
heres the best test.

does compiz work?

can you watch video?

does google earth work (if installed)?

Can you see anything that looks like the Ubuntu gnome desktop?

If you answered yes to these questions your fine

otherwise open a terminal and see if this command works
```
glxgears
```

---

### Post by emeraldgirl08 on 2009-05-06
lol yeah that was an obvious answer. I did think about that. I just got done reading some threads and when that happens I wind up with new ideas along with questions. Some people are reporting their ATI problems and while I have an ATI card I can enable Compiz and with only 16 MB of VRAM I can spin the cube etc.

It's just some little things like scrolling in firefox and occasional page rendering that come out choppy. Yeah the Video card is ancient but it seems more smooth in that other OS. I'm still using linux most of the time because ,quite frankly, I feel comfortable with it.

Just thought I'd ask :)

Thanks.

---

### Post by feelshift on 2009-05-06
```
glxinfo
```
Check out the "direct rendring" line. It should be be "Yes"
```
glxgears
```
This runs a graphic test. Wait for about 30 second and then check what fps you get. On my nVidia 8500GT 1GB I get ~500 fps in fullscreen.

---

### Post by emeraldgirl08 on 2009-05-06
I ran the glxgears code and got this as a result (I cut it off after four or five minutes; didn't' know what to do with it).

:~$ glxgears
2559 frames in 5.0 seconds = 511.737 FPS
3575 frames in 5.0 seconds = 714.795 FPS
3370 frames in 5.0 seconds = 673.851 FPS
3411 frames in 5.0 seconds = 682.127 FPS
3340 frames in 5.0 seconds = 667.955 FPS
3412 frames in 5.0 seconds = 682.336 FPS
3388 frames in 5.0 seconds = 677.516 FPS
3406 frames in 5.0 seconds = 681.076 FPS
3387 frames in 5.0 seconds = 677.374 FPS
3404 frames in 5.0 seconds = 680.580 FPS
3383 frames in 5.0 seconds = 676.560 FPS
3410 frames in 5.0 seconds = 681.912 FPS
3382 frames in 5.0 seconds = 676.397 FPS
3407 frames in 5.0 seconds = 681.312 FPS
3171 frames in 5.0 seconds = 634.068 FPS
3381 frames in 5.0 seconds = 676.053 FPS
3262 frames in 5.0 seconds = 652.391 FPS
4444 frames in 5.0 seconds = 888.731 FPS
7785 frames in 5.0 seconds = 1556.948 FPS
7662 frames in 5.0 seconds = 1532.191 FPS
4262 frames in 5.0 seconds = 852.339 FPS

And in fullscreen

~$ glxgears
2459 frames in 5.0 seconds = 491.428 FPS
637 frames in 5.0 seconds = 127.272 FPS
762 frames in 5.0 seconds = 152.350 FPS
760 frames in 5.0 seconds = 151.987 FPS
762 frames in 5.0 seconds = 152.343 FPS
761 frames in 5.0 seconds = 152.060 FPS
762 frames in 5.0 seconds = 152.329 FPS
759 frames in 5.0 seconds = 151.683 FPS
762 frames in 5.0 seconds = 152.285 FPS
761 frames in 5.0 seconds = 151.985 FPS
761 frames in 5.0 seconds = 152.162 FPS
761 frames in 5.0 seconds = 152.067 FPS
762 frames in 5.0 seconds = 152.278 FPS

These were done with pidgin and firefox on. Don't know if turning everything off would have made a tremendous difference.

---

