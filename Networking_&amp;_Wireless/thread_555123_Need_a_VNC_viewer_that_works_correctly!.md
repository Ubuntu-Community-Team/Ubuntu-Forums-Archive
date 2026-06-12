---
title: "Need a VNC viewer that works correctly!"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2007-09-19
I have a windows PC that is running TightVNC Server that is using the "Add Client" feature to basically start a reverse VNC session to me, running Ubuntu on my end.

I've used the standard vncviewer -listen -fullscreen command, and that works decent, but there is a terrible amount of video noise that require screen refreshest to get it all clear again.  So there must be some kind of mismatch between encoders or something.

So then I found xtightvncviewer.  It has a fullscreen option and seems to perform a lot better than the standard vncviewer included with Ubuntu, but when I'm in fullscreen mode, I don't have any control of the keyboard.

According to the MAN for xtightvncviewer, you are supposed to be able to add a -grabKeyboard option at the command line, but it then tells you that it's not a valid option.

All I'm looking for is a viewer that will accept these incoming sessions from tightvncserver on windows PC's and get a stream of video that looks smooth and not like a bunch of compressed video noise.

---

