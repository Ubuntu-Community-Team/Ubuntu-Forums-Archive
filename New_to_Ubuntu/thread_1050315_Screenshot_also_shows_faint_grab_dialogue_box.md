---
title: "Screenshot also shows faint grab dialogue box"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by loobyloo on 2009-01-25
Hi
I've just tried to take a screenshot and you can see the dialogue box.  

[http://tinyurl.com/cpjo26](http://tinyurl.com/cpjo26)

Apart from work-rounds like moving it into the corner or something, is there a way of making the dialogue box disappear in the final image?

---

### Post by desperado665 on 2009-01-25
try taking a timed snapshot

---

### Post by Dr Small on 2009-01-25
Are you running Compiz-Fusion? It looks like the window is slowly faiding out while pressing PrintScreen.

---

### Post by SunnyRabbiera on 2009-01-25
Yeh this is an old problem, seems to be linked to the way the screenshot tool is rendered.
A way around this is to install ksnapshot, or use the screenshot tool in the gimp.

---

### Post by pi.boy.travis on 2009-01-25
It is likely because of Compiz Fusion.  It is easier to set a timer than to turn off Compiz.

---

### Post by SunnyRabbiera on 2009-01-25
> **pi.boy.travis said:**
> It is likely because of Compiz Fusion.  It is easier to set a timer than to turn off Compiz.

or use the gimp, its screenshot tool is just as good.

---

### Post by loobyloo on 2009-01-25
Woo, that was fast!  Thanks - the delayed screenshot idea worked but I'll look into the other suggestions as I won't remember to delay it all the time.

Thanks folks!

---

### Post by loobyloo on 2009-01-25
SunnyRabiera - where's the screesnhot grab tool in Gimp?  Googling, someone said it's in File>Acquire>Screenshot but I can't seen an option by that name there in Gimp 2.6.1

TIA

---

### Post by llamabr on 2009-01-25
File > Create > Screenshot

Also, you could try scrot, which runs on the command line:

brock@vader:~/Desktop$ apt-cache search scrot
scrot - command line screen capture utility
brock@vader:~/Desktop$

---

### Post by thraxy on 2009-01-25
Well, if you want a fullscreen screenshot, you can just use the PrtSc button. That should make a screenshot without opening the selection box. It will only ask what name you want to save it as.

Also, if you have Compiz enabled, it's a good idea to enable the screenshot option in there. That way if you just want to make a screenshot of a small selection of the screen, you can use super+leftclick and drag a selection around the area you want. I find that feature very handy when I just want to send someone a small picture of what I'm working on in GIMP or a piece of an IM convo.

---

### Post by kostkon on 2009-01-25
> **llamabr said:**
> File > Create > Screenshot

Also, you could try scrot, which runs on the command line:

brock@vader:~/Desktop$ apt-cache search scrot
scrot - command line screen capture utility
brock@vader:~/Desktop$
Or a GUI app based on it, [*GScrot*]("https://launchpad.net/gscrot"), if you like. It is very good.

---

