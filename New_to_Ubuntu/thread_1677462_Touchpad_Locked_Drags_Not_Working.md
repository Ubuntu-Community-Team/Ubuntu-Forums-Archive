---
title: "Touchpad Locked Drags Not Working"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by KlytusLord on 2011-01-28
Hi all,

After some research, I found this guide:
[http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)

I have Ubuntu 10.04 so I followed the instructions using the touchpad.rules approach. My file looks like this:

ACTION!="add|change", GOTO="touchpad_end"
KERNEL!="event*", GOTO="touchpad_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="touchpad_end"
ENV{x11_options.LockedDrags}="1"
LABEL="touchpad_end"

Sadly, I am still not getting the locked drags option to work.

Any suggestions?  Thanks.

---

