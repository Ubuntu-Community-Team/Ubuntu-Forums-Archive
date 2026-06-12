---
title: "Crashes! Someone please help a newbie!"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by mac98aop on 2009-01-09
Hi there

Running 8.04 on Dell Mini 9. Keeps crashing. No rhyme nor reason. Full crash and the whole screen freezes. Hard reset only option. 

Read other threads. People mention looking at top and Xorg data?

I did tinker with the unit when I first got it, installing Compiz etc. Have totally uninstalled that now. However, my title bars still look 'prettier' than when unit fresh out the box?

Is there any way of putting things back to factory settings without a full reinstall?

Can someone help diagnose if I've mucked it up? Is there a crash log that gives a clue what is causing it?

PLEASE HELP!

---

### Post by The Tronyx on 2009-01-09
You may want to look into /var/log/messages or /var/log/syslog but I am guessing /var/log/messages would be of most assistance.  I would recommend trying to find timestamps which correspond with the time of the crashes on your machine.  Best of luck!

---

### Post by mac98aop on 2009-01-09
Thanks but.... if I type either of those into the terminal it just says Permission Denied? Now what?

---

### Post by Captain_tux on 2009-01-09
Type **sudo** then the command...

---

