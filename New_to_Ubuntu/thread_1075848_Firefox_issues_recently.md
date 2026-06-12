---
title: "Firefox issues recently"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by unknown user on 2009-02-20
[FONT="Tahoma"][COLOR="Blue"]I have been having a few issues with Firefox, which are hard to describe, but I will try. They are not constant, but more often than not.
When I open Firefox it does not have the bar at the top with the cross in the right hand corner, so I am unable to close it down without clicking on File and then close or quite. 
If I open another window it looks like it closed down and I have to tab to it. When I move over to the left or the bottom of my screen, the bars do not come up. It is like Firefox has taken over the whole of the screen and I can not move away from it.
As far as I am aware, I have not changed anything in my settings. Does anyone know anything about this?[/COLOR][/FONT]

---

### Post by perpetualcacophany on 2009-02-20
I'm pretty sure I know the problem you're talking about. Try this:

Get CCSM if you don't have it.

```
sudo apt-get install compizconfig-settings-manager
```

Open it when it finishes open it through System -> Preferences -> Compiz Config Settings Manager

Scroll down to the Utilities section and open up Workarounds

In the window that opens uncheck "Legacy Fullscreen Support"

That should fix it.

---

### Post by unknown user on 2009-02-20
[FONT="Tahoma"][COLOR="Blue"]My gosh, thank you ever so much for the fast reply to something that has been driving me mad for the last few days. I was really shocked at how quick you replied to this thread and that it worked, honest cheers, perpetualcacophany. [/COLOR][/FONT]

---

