---
title: "messed with CompizConfig in Unity: now no shortcuts/dock/etc (how to reset??)"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2011-05-04
So I was messing with my new Ubuntu setup (11.04 unity) in which case something I did (in switching from wall/cube etc etc) caused everything upon restart to be gone (cant do keyboard shortcuts, cant open launcher, cant open anything, cant ctrl-alt-t for terminal. But i **can** left click on desktop.

Any suggestions on how to reset things? 


Note: everything is okay when loading in "low graphics mode" (at least without Unity and into Gnome).

---

### Post by 5149.5 on 2011-05-04
Here is something you can try that has worked for me. Press Alt+F2. Even if nothing happens, go ahead and type in ```
unity --reset
```Cross your fingers and press enter. You may see some disk activity and in a few seconds, your desktop will return.

---

### Post by UbuNoob001 on 2011-05-04
> **5149.5 said:**
> Here is something you can try that has worked for me. Press Alt+F2. Even if nothing happens, go ahead and type in ```
unity --reset
```Cross your fingers and press enter. You may see some disk activity and in a few seconds, your desktop will return.


success! Though one of the processes that seemed to take place upon issuing the command kept going on forever (something about window (of a recently opened application) doesn't fit screen etc). So I terminated, but everything seems alright. 

Thanks.

---

### Post by 5149.5 on 2011-05-04
I'm glad it worked for you.

---

