---
title: "[SOLVED] Why VNC client is so much slower on ubuntu than on XP"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by jalmargyyk on 2008-04-24
I was having problems with VNC client being much slower on ubuntu than on XP. This issue was covered in [this]("http://ubuntuforums.org/showthread.php?t=764117") thread.

The solution to this problem was easy as usual. :redface:

I didn't remember that I had enabled remote desktop (vino) on my computer a few months ago for testing purposes. Unfortunately I had forgotten it to run on background. It was somehow messing all the connections to different ports (5900, 5901, 5902) even I had made ssh port forwarding as follows:

ssh [email]test@example.com[/email] -L 5901:example.com:5900

So, everything I did was stop sharing my desktop via vino and after that speeds were comparable to XP.

---

### Post by Dysan911 on 2008-09-12
I wish I could say mine was a simple fix like that..   I do not have anything like RDP turned on however if I VNC from XP.   I have a fairly decent performance to work remotely..  If I connect via VNC from my Ubuntu..  It's a SLIDE SHOW and completely unusable.

Ive searched and surprised to find very little on how to resolve this..     

Booooooooo!


:)

---

### Post by the real omni on 2009-01-03
This thread should either be renamed or should have the [SOLVED] removed from its title.

I have similar issues with VNC's latency - when I VNC into my XP machine from another XP machine, VNC is super fast. When I VNC into my XP machine from an Ubuntu machine, VNC takes about 1 minute of redrawing the first screen before I can use it, and then unless I disable the desktop image and reduce the colour depth, it very slowly draws the screen whenever I move the mouse or anything like that. Very very poor performance.

If this thread is going to remain solved, the title should be changed to "My VNC problem" or something to illustrate that the only thing solved is jalmargyyk's vino problem.

The problem of VNC being wayyyy slower on Ubuntu than on XP is still unsolved.

---

### Post by Dysan911 on 2009-01-03
> **the real omni said:**
> This thread should either be renamed or should have the [SOLVED] removed from its title.

I have similar issues with VNC's latency - when I VNC into my XP machine from another XP machine, VNC is super fast. When I VNC into my XP machine from an Ubuntu machine, VNC takes about 1 minute of redrawing the first screen before I can use it, and then unless I disable the desktop image and reduce the colour depth, it very slowly draws the screen whenever I move the mouse or anything like that. Very very poor performance.

If this thread is going to remain solved, the title should be changed to "My VNC problem" or something to illustrate that the only thing solved is jalmargyyk's vino problem.

The problem of VNC being wayyyy slower on Ubuntu than on XP is still unsolved.



I 2nd that bigtime!

---

### Post by the real omni on 2009-01-04
Okay here's something to validate the [SOLVED] tag for this thread:

The problem is that the RealVNC server sucks. No matter what linux VNC client you use, if you're running a RealVNC server on your XP machine you WILL experience terrible latency.

The solution: scrap RealVNC altogether on the XP machine and install TightVNC. 

I replaced Real with Tight on my XP machine and now Vinagre (the linux VNC client) has no latency issues at all... It's actually usable!! And fast!

So basically, I hereby flip the bird to RealVNC and wholely endorse using TightVNC as the new standard in VNC server software for cross-platform uses.

---

