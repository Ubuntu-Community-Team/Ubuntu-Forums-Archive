---
title: "can't drag windows to other monitor"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by brdohman on 2009-11-10
I'm running compiz-fusion on Ubuntu 9.10 amd64. I have dual monitors setup and have the desktop cube enabled. However, I cannot drag windows/browsers/anything from one monitor to the other. I've looked through the compiz-fusion settings and haven't found a way to allow me to drag across monitors. 

Also, on the 2nd monitor, there is the two panel bars. Whenever I launch a program from the panel bar on the 2nd monitor, it opens on monitor one. However, nautilus windows will stay on the 2nd monitor when opened there.

Thanks in advance.

---

### Post by ekztal on 2009-11-23
I've having the same problem, I did my first install of Ubuntu 9.10.

At first I had both monitors showing the same image, and I unchecked, "Mirror Screens" in the Display settings.  I logged out and back in and it worked.  

I just logged on again after setting up grub and seeing if it was setup right and now my mouse is stuck on the secondary monitor unless I open a window and drag it over to the first monitor.  My mouse is then finally able to move over but then any windows I try to move will only go 4/5th the way over to the first monitor.


When I say first and secondary monitor, the first has the 2 panels at the top and bottom.  Secondary is just a blank desktop.

---

### Post by pnhoang on 2009-12-29
I have the same problem.  The trick to get over this problem is open "Display" (System => References => Display), then choose Mirror, apply it then close.  Open Display again, this time set turn off Mirror, apply and close.  You should be able to drag windows to second monitor now.
I have no idea how it works but that's how I get over this problem.

---

### Post by audiomick on 2009-12-29
Hallo.
You need to bear in mind the different ways that the system can use 2 monitors.
The extended desktop that is possible in windows is provided by the xinerama function. nVidia has their own solution, that they call "twinview". If you are using twinview, the xinerama function has to be off. 

Apart from that, there is the mirror mode, which simply puts the same screen onto both monitors.

What is also possible, which I don't think has an equivalent in windows, is that the system can put out a completely independent screen on each monitor. I had this going at one point, but never figured out how to specify which screen the mouse and keyboard belonged to.

Maybe the system is getting mixed up between modes.

---

### Post by natravis on 2009-12-29
I encountered a similar problem while I was using my laptop to show my parents the awesomeness that is Dexter. My fix was to edit the xorg.conf file because I found that while it had a reference saying that the TV was to the right of the laptop, it did not have one saying the the laptop was to the left of the TV, and so once I got on the TV, it would no longer come back to the laptop. Hope this helps.

---

### Post by dogtato on 2012-06-17
> **audiomick said:**
> Hallo.
You need to bear in mind the different ways that the system can use 2 monitors.
The extended desktop that is possible in windows is provided by the xinerama function. nVidia has their own solution, that they call "twinview". If you are using twinview, the xinerama function has to be off. 
Thanks for this post. In hindsight, it seems obvious that "Separate X screen" was the culprit, but I didn't know what TwinView meant and it didn't even occur to me to try it since it sounds like it means "mirror"

I had a separate issue with my second monitor not being detected that I had to resolve by plugging in just the digital, restarting, then plugging in the analog too and restarting. Between that and the "can't drag" issue I was in some dismay over Ubuntu's multi-monitor support, but I managed to get it fixed in about an hour of messing around.

Your post was the only useful information I found from several google searches. Everything else just said to "turn them on in nvidia settings" or worse, "turn them on in display settings"

---

### Post by overdrank on 2012-06-17
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

