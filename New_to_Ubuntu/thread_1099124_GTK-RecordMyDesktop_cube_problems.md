---
title: "GTK-RecordMyDesktop cube problems"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by Cfhs_1 on 2009-03-17
Hi, I love the idea of good working screen recording software, but when it comes to Ubuntu this area is...well, lacking. the only screen recorder I could get to work is recordmydesktop. it works okay, but every time I try to record my desktop cube effect it looks horrible. I have all the restricted drivers installed for my graphics card, but it still does this. Is there anyway possible to fix this? (I really want to make a video of Ubuntu effects so I can show it off to all my friends who are still convinced Windoze is the best.) :D I posted a link to a video of the problem below.


                                               Any help will be appreciated,
                                                           Nicholas C. Brown


[http://www.youtube.com/watch?v=uMSwAzZlWbg](http://www.youtube.com/watch?v=uMSwAzZlWbg)

---

### Post by Temposs on 2009-03-17
There are other programs that do the same thing. You could try them and see if you get a better result. The alternative one I'm finding in the Add/Remove program is:

Istanbul Desktop Session Recorder

---

### Post by Cfhs_1 on 2009-03-17
I'll try it. thanks!

---

### Post by Cfhs_1 on 2009-03-17
Istanbul does the same thing...could it be my processor? I'm using a p4 at 2.80Ghz.

---

### Post by sebeto on 2009-08-15
I've got exactly the same problem... Does anyone have a solution?

I have a Core 2 Duo T9300 2.5GHz, a Geforce 8600GT MXM (nvidia drivers 180.44), 3Go of RAM... Everything works perfectly fine, except when trying to record the rotating cube, some strips and problems appear...

I tried with gtk-recordmydesktop and xvidcap, always the same problem...

If anyone has a clue on how to solve this problem...

---

### Post by sebeto on 2009-08-15
Ok, if you have a nvidia graphic card I think that I found how to solve the problem: launch nvidia-settings, and in OpenGL settings uncheck "allow flipping".

Now it works very well for me.

---

### Post by diablo75 on 2009-08-15
Istanbul is much worse than gtkrecordmydesktop, in my opinion.

There is a preferences panel in gtk-recordmydesktop with an option that says "Full shots at every frame".  I can't promise you this will solve your problem, but you may see an improvement.  In my experience, you have to have some killer hardware for it to record flawlessly.  Though I've never tested it out on any Intel based graphics chipsets; only nVidia.

---

### Post by blur xc on 2009-08-20
I tried record my desktop for the first time last night and had a few issues.  Tearing of the cube wasn't too bad, but mostly lost a lot of my compiz functionality.

First- Expo only worked half way.  Super-E initiated it, but I couldn't drag any open windows from one desktop to the next.  I had scale enabled (like Mac OSx Expose) by clicking on the bottom right corner of my screen, but it wouldn't work.  The key binding (I think it was Alt-Shift-UpArrow) worked though.  That, and there were a few other similar issues.

In regards to "Full shots every frame", do I want it on, or off?

thanks,
BM

---

### Post by squeekyclean on 2010-07-10
RecordMyDesktop worked perfectly well for me in recording my desktop rotating cube. You may have to enable the "Allow Flipping" in the OpenGL Settings of your video card(mine is nVidia).

I tried RecordItNow and Istanbul. They both can't record the rotating cube even if I set both settings to the highest quality(maximum frames per second,etc.). 

Maybe you could try remote desktop viewers instead, and let them record your desktop from another location, maybe that'd work as a last resort, with low quality results though. :D

Good Luck:)

---

