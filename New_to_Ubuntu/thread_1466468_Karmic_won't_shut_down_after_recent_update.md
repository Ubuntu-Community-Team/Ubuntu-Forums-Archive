---
title: "Karmic won't shut down after recent update"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by heykev on 2010-04-30
Use Karmic.  Love it.  Recently accepted an update that required a reboot.  Since then, the system hangs during shutdown.  Sometimes it displays a black screen.  Sometimes I get a lot of terminal-looking text that appears to describe the shutdown process, but at that point the keyboard lights have gone off and the computer accepts no input.

System working fine other than shutdown.

Help appreciated!!

---

### Post by Bodsda on 2010-04-30
> **heykev said:**
> Use Karmic. Love it. Recently accepted an update that required a reboot. Since then, the system hangs during shutdown. Sometimes it displays a black screen. Sometimes I get a lot of terminal-looking text that appears to describe the shutdown process, but at that point the keyboard lights have gone off and the computer accepts no input.
 
System working fine other than shutdown.
 
Help appreciated!!
 
I would try running the shutdown from the terminal
```

sudo shutdown -P now

```
 
If this fails, you should see the error and then can inform us of what it is.
 
Bodsda

---

### Post by heykev on 2010-04-30
Thank you Bodsda.  I ran your code and the machine shuts down much as it would if I used the shutdown button on the panel.

Currently, that means I get to see the black background with the whitish/grayish ubuntu symbol in the middle of the screen, then the screen goes completely black and the machine hangs.

So I have no terminal readout to report.  Is there perhaps a log file I could provide?  I don't know if/where that exists, but if you can direct me I could probably get it cut/pasted into a posting here.

---

### Post by heykev on 2010-05-03
Anyone able to help me troubleshoot this?

I guess I need to find some sort of shutdown log file and post it's contents here, but I'm not sure how to do that.

Thanks!

---

