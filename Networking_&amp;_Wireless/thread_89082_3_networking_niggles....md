---
title: "3 networking niggles..."
date: 2005-11-11
forum: Networking &amp; Wireless
---

### Post by Tadhg on 2005-11-11
Three things i have to ask about regarding my laptop and wireless.

First, at startup, it seems to hang at configuring network devices. Usually for up to a minute or so. Any way of helping it along/stopping it hanging?

Two, and probably related, is there anyway of getting ubuntu to recognise the card when i insert it, i.e. being able to just plug in the wifi card at anytime when ubuntu is running and have it pick it up? It worked in windows, and will save me having to restart all the time. 

Related to the other questions, anyway around having to ifup and ifdown upon startup to get a wireless connection? Would be handy.

Anyway, hopefully someone can help me to get to a nice clean wireless setup.

---

### Post by adwait on 2005-11-11
If I am not mistaken, hotplug is the application that detects new hardware. So when you plug in the wireless card, instead of restarting the computer, you can just
```
sudo /etc/init.d/hotplug restart
```

Not very sure about this though......bit worth a try.

If you need to ifup ifdown every time you start the computer. I suggest you make a script and put it in the /etc/init.d/ directory and then using rcconf select to make it execute on start up. (If you don't get any of that.....just search on how to make a start up script or post here and Ill post the detailed instructions.)

---

