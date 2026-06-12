---
title: "QuadraPassel does not start"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by itsols on 2011-01-23
Hi, does anyone have the same problem? Quadrapassel does not work on my OS (10.10).

SuperTux works without a problem. Many others too...

When I click on the program, it says 'starting quadrapassel' in the task bar but then vanishes. Nothing comes up.

Any ideas?

---

### Post by kellemes on 2011-01-24
Start it from a terminal-window and post the output, maybe we can work with that.

---

### Post by itsols on 2011-01-24
Thanks for that idea. Here's the output after it being launched from the terminal:

failed to create drawable
Failed to initialise clutter: Unable to select the newly created GLX context

---

### Post by kellemes on 2011-01-24
Can only point you the the relevant bugreport.. seems you're not the only one with this issue.
Maybe you can find some usefull pointers in the thread?
Good luck.
Bugreport..
[https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/561734]("https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/561734")

And another bug that may be relevant..
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/654361]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/654361")

---

### Post by wb6vic on 2011-03-06
same problem here -- and I love tetris!

---

### Post by itsols on 2011-03-06
I never really got QuadraPassel working. I gave up on it. But here's the GOOD NEWS. If you love tetris, here's another program like it in the repos - LTris. This works!

Cheer up!

---

### Post by syntr on 2011-03-06
Yeah, a few of the Gnome games have bugs in Ubuntu

Gnibbles doesn't work either

---

### Post by itsols on 2011-03-06
I think it's not about some games not working... Rather, it's to do with some of our graphics cards and incompatible drivers. For one sure thing I know that Intel graphics have issues (like with my laptop). But there are 2 PCs at my place with different graphics cards and they're just fine.

Also (for example), my Ubuntu themes with animations don't work. But it's ok I guess since I'm not too keen in a fancy desktop. Just the basics are sufficient.

---

### Post by Nithogger on 2011-08-06
Hey guys,

I had the same prob, came here. Looked around and heard some guy talking 'bout graphical drivers. I recalled that i installed missing drivers (can be found in the System/Administration/Additional Driver section). So I tried Quadrapassel out for the first time in ages. And guess what it worked. SO.. I suggest people start activating there drivers (can be done in the same menu as given earlier) and restart your laptop/computer and happy tetressing... :D And yes, the LTris version is good as wel. 

Cheers lads.

---

### Post by itsols on 2011-08-07
@Nithogger, thanks for your tips, but it's like a 'proven fact' that my Intel graphics have issues with my OS. I've tried everything to-date. So I guess I'll stick to LTris, if at all.

On the other hand, MAYBE the new release of Ubuntu will have some patches fixed. Right now I'm waiting for the countdown until my current release stops any updates in April. Then I think I'll see what Natty has got in store. But for now, my 10.10 is just marking time.

On a different note, LTris is not so good for little kids. They prefer the old QuadraPassel for simplicity.

Thanks for sharing your thoughts anyway.

---

### Post by candtalan on 2011-11-06
With Ubuntu 11.10 Oneiric 

On three machines 
- an old laptop using ubuntu 2D: quadrapassel does 
not start

- a not so old, but single processor PC: not start
(terminal shows response 'segmentation fault')(kblocks works well)

- more recent machine, quad core,  it runs ok

---

