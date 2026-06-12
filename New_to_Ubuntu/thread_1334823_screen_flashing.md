---
title: "screen flashing"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Chris Edgell on 2009-11-22
Can any ONE speculate as to why my screen keeps (off and on) flashing?
It's not constant, but intermittent and sporadic. {Earlier I thought it was gone--but it's back}

Any advise?  Just turn it off and talk to my contact?  Or wait until maybe it freezes up?

---

### Post by werecatomega on 2009-11-22
i don't understand what you mean when you say your screen is flashing? explain so i can understand your problem better

---

### Post by Chris Edgell on 2009-11-22
It's almost like an erratic strobe effect.  On my desktop page, which shows the effect better because it's dark blue: it flashes like someone is taking a photo, it's an effect, like a strobe light.  There is a flash of ghosting, almost like trails...there's quite a frequent jiggle to the picture too.

---

### Post by Chris Edgell on 2009-11-22
Picture this: 

Imagine that your computer screen is a picture laying in a pan.  People are taking photos and the picture reflects all the flashes of the cameras.  Then somebody shakes the pan vigorously.  The whole picture quivers, shifts, and flashes.

Can you imagine my screen with THIS description?

I wonder if it's my monitor "going".

---

### Post by cariboo on 2009-11-22
I've run into the same thing, when booting the Live CD and when trying to chnge the color depth in /etc/X11/xorg.conf.

On the computer I was having the problem with I have an Nvidia 8400GS connected to a KDS VS-190 crt monitor. To solve the Live CD problem I just started in Safe Graphics mode. The problem only happens with this combination. 

To fix the color depth problem, on a different computer with a Nvidia 9400GT connected to an Acer LCD monitor. I had to start in recovery mode and copy /etc/X11/xorg.conf to a backup:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

While at the root prompt I run:

```
nvidia-xconfig
```

To recreate a working xorg.conf file and then continue on to the desktop.

---

### Post by Chris Edgell on 2009-11-22
Oh, Cariboo,
Thanks for the response.
If I understand you correctly your approach to the problem involves having 2 computers.  If that's the case I'll have to save your proposed solution for when I have the chance to see the guy who set me up on this computer.

If I have misunderstood then you must bear in mind that I'm not just a beginner, I'm also SO unclear on the concepts....I grapple and barely grasp....

If this is something I can try on my terminal, try to issue me step-by-step instructions and I'll give it a try.

Thanks again!
Chris

---

### Post by RedRat on 2009-11-22
A bit more info about your system would be helpful here. Are you using an old CRT display or LCD display. What kind of graphics card are you using.

If it is a CRT display, sounds like it might be on its last legs. The same might be true for an LCD monitor too. However, unless we know something about your graphics card and driver, it will be just guessing about what might be wrong here.

---

### Post by Chris Edgell on 2009-11-22
RedRat,
Do you have the time and patience to tell me how to ascertain the answers to the questions you have asked?  I have been able to follow explicit instructions with going into the terminal etc.

---

### Post by RedRat on 2009-11-22
Well the first question is whether you are using a Cathod Ray Tube (CRT) display vs a flatscreen LCD. If the monitor is a very think, about an inch thick, it is an LCD, if it is big humongous box and weighs quite a bit, it is a CRT. That would help us right off.

Years ago, my old Sony monitor began acting up and then one day it just did not turn on. A bright flashing of a CRT indicated that something is wacko with the internal magnet deflectors. LCD, I suppose, might well behave the same way since they are backlit with fluorescent tubes. One or maybe all are giving up the ghost. Much depends on how old your monitor might be, they don't last forever. Same goes for graphics cards. How old is this computer you are using? All of this helps here.

---

### Post by Chris Edgell on 2009-11-22
It is a CRT.  Yes, the humongous one.

Internal magnet deflectors...that kinda' resonates in my intuition.

The computer is a reconditioned one I got from a friend of mine--he reconditioned about 10 from a school.

The monitor is a dell that I got a year ago  On the back it says that the Chassis was manufactured in 1997...I was shocked by that.

I must admit that I laid my hand on it by chance a few days ago and noticed that it was warn and when there was talk about shutting down your computer or leave it running, someone mentioned burning something up.  It did cross my mind that I have done wrong leaving it on.  (I'm sure I should have known that it shouldn't be on all the time.  I can just have the most absurd gaps in intelligence...such as it is when it's present...)

Oh, now I know why it had stopped for a couple of hours...because I had turned it off for the first time in weeks.  I think I'll turn it off in about a half an hour and then just turn it on once a day and then turn it back off when it begins flashing, and just see how long I can make it last.

Thanks...now I'm very sure I understand...it is this.

---

### Post by JohnnyVW on 2009-11-22
> **RedRat said:**
> A bit more info about your system would be helpful here. Are you using an old CRT display or LCD display. What kind of graphics card are you using.

If it is a CRT display, sounds like it might be on its last legs. The same might be true for an LCD monitor too. However, unless we know something about your graphics card and driver, it will be just guessing about what might be wrong here.

I have to agree with RedHat.  I had a CRT do this same thing several years ago.  Scared the *stuff* outta me!  :o

---

### Post by Chris Edgell on 2009-11-23
So this IS solved.  I have just turned it all off for an hour and now that it's cooled it's not flashing at all.  [I need to learn to think through things sooner rather than later...at the first sign of trouble, I could put my mind to it--what can I say now, better late than never.]

Again, I thank all.

---

### Post by RedRat on 2009-11-23
> **Chris Edgell said:**
> So this IS solved.  I have just turned it all off for an hour and now that it's cooled it's not flashing at all.  [I need to learn to think through things sooner rather than later...at the first sign of trouble, I could put my mind to it--what can I say now, better late than never.]

Again, I thank all.
No problem, glad that we could help. However, I would take it as a warning sign that perhaps the monitor is on its last legs. With "Black Friday" coming up, you might find a good deal on a new LCD monitor.

---

