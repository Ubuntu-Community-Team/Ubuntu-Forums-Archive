---
title: "Annoying problem!"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by jeff91 on 2010-08-10
I don't know how this happened...

I could have gone on a site which could have downloaded something onto my computer to make this happen, or maybe someone might have messed with it.  In the end, I can't be sure.  All I know is that I would like to fix this problem as soon as possible.

I tried a screen-shot so that you'll see the problem but everything on it came out okay.  The screen-shot was normal and it failed to show the problem.

Here's the problem:  the screen in front of me has become overly elongated and it curves inwardly (left and right sides).  Furthermore, every window that I open has an inwardly curve to it.

I've been trying to fix this for the last 2-3hrs to no avail.  Please help! 

PS:  I even reinstalled the OS.  Nothing helps.

---

### Post by sydbat on 2010-08-10
> **jeff91 said:**
> I don't know how this happened...

I could have gone on a site which could have downloaded something onto my computer to make this happen, or maybe someone might have messed with it.  In the end, I can't be sure.  All I know is that I would like to fix this problem as soon as possible.

I tried a screen-shot so that you'll see the problem but everything on it came out okay.  The screen-shot was normal and it failed to show the problem.

Here's the problem:  the screen in front of me has become overly elongated and it curves inwardly (left and right sides).  Furthermore, every window that I open has an inwardly curve to it.

I've been trying to fix this for the last 2-3hrs to no avail.  Please help! 

PS:  I even reinstalled the OS.  Nothing helps.One of 2 things - your monitor is dying or someone played with the monitor settings.

---

### Post by bazzal1941 on 2010-08-10
Interesting, so the processes which display the screen think everything is ok so maybe it is hardware as suggested. That means either the monitor or whatever is controlling the graphics. Is there some setup process for your graphics controller that may be of use?

---

### Post by badbradmx on 2010-08-10
annoying thread title, please put up basic details in the title next time

that being said it looks like dodgy settings or a dodgy monitor

---

### Post by marshmallow1304 on 2010-08-10
Look for buttons on the monitor.  One should open a menu where you should be able to change settings for concavity, among other things.

---

### Post by jeff91 on 2010-08-10
[QUOTE="sydbat"]One of 2 things - your monitor is dying or someone played with the monitor settings. 	[/QUOTE]

If it's the latter, how do I fix it?  I tried fixing it by messing with the monitor setting ("pincushion" is on "51."  When I try to change it, it does nothing) but I messed things up even more and that's why I had to reinstall the OS.  After I reinstalled the OS, it's back to being like it was when the problem first started (yesterday).

---

### Post by badbradmx on 2010-08-10
is this a laptop or desktop? if you have an external monitor, fiddle with those settings, you can always restore those easily.

---

### Post by rollin on 2010-08-10
I think it is hardware. I clicked on a bad link once on a fantastic site where my graphics on the desktop melted away to an unreadable state, after re-installation all was well.

Probably your best bet is to post your monitor details as someone here may have the same one too. Check the monitor name against launchpad bugs via Google etc.

Edit: Also check for bugs with your graphics card too. You can find the info on this via a terminal copy and paste (w/o quotes) "lspci | grep VGA".

---

### Post by badbradmx on 2010-08-10
also if possible try a different monitor, seems obvious to try but it will eliminate something. that being the monitor or hardware

---

### Post by jeff91 on 2010-08-10
I'm using a hp pavilion mx703.

Here are some of my monitor settings:
 
Size/Position ->H Adjustment -> H Size - 53 
                                             -> H Position 50 ->
                     -> U Adjustment -> U (or V - I can't tell)Size - 53  
                                             -> U (or V) Position 50
                     -> Zoom ->  Zoom - 53
 
 Advanced -> Color ...
                 -> Image rotation -> 50
                 -> Image shape -> Trapezoid - 51
                                         -> Parallelogram - 53
                                         -> Pincushion - 51
                                         -> Pincushion balance - 4
                  -> Moire correction -> Moire correction - yes
                                               -> U (or V) Moire - 0
                                               -> H Moire - 49
                   -> OSD settings -> Lock OSD settings - no
                                             -> Timeout - 60s
                                             -> U (or V) Position - 50
                                             -> H Position - 50

The above didn't come out the way I intended it to but I hope it helps nonetheless.

---

### Post by badbradmx on 2010-08-10
based on that monitor id upgrade to an LCD, better quality and easier on the eyes. have you got access to a spare monitor cos like i said that would eliminate one side of the problem. if its the monitor then the picture on the spare (or a friends) will be fine but if the image is still warped then its shows its an internal problem.

other than that wiser heads are required, im no expert, just like throwing ideas out there :)

---

