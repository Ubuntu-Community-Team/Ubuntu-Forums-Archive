---
title: "Printing"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by jnmjr on 2010-02-08
Hey Guys, can't print from Ubuntu, printer Cannon MP830 has worked from day one, checked it in WinXP and printing is fine so its not the printer, Karmic seems to be up to its funny stuff, any ideas?

---

### Post by patchwork on 2010-02-08
You say the printer was working and suddenly stopped? 

Is the cups service running?  ```
ps -fu root | grep cups
```

I had an issue at one point where cups would not start without manually starting it.  I ended up working around the issue using monit to automatically check the status and restart if necessary.

---

### Post by jnmjr on 2010-02-08
> **patchwork said:**
> You say the printer was working and suddenly stopped? 

Is the cups service running?  ```
ps -fu root | grep cups
```I had an issue at one point where cups would not start without manually starting it.  I ended up working around the issue using monit to automatically check the status and restart if necessary.

It seemed running Ok, what I did, I went to Synaptic installed everything that said "CUP", re-started and now I'm printing again. THX for the CUP info I didn't know about it. I'm closing this thread but I'm keeping my fingers crossed.

---

