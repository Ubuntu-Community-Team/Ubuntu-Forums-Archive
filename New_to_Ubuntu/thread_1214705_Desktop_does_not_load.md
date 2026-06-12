---
title: "Desktop does not load"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by pibbTibbs on 2009-07-16
Hi all

So i had my first ubuntu install attempt last night on my asus eee900. Everything went perfect and was working great last night except for choppiness exhibited on the net book launcher application (apparantly this is a known bug with GL and the intel 915m chip) anyhow i switched to the classic dektop, played around for a little bit and did all of the updates it had listed.

This morning I boot it up but the desktop wont show, just the background wallpaper and the cursor. If i right click i can get some options ie. Create Folder, Creat Launcher Etc. But no start bar or anything else.

Does anyone have a solution to this before i try to re-install tonight. I am a complete linux noob so i am not sure as to what else can be tried before re-installing again.

Thanks
J

---

### Post by ptn107 on 2009-07-16
It may be a gnome desktop problem.  You can try wiping gnome's settings and going back to the system defaults if you can get to a terminal:
```
cd ~ && rm -r .gconf/ .gconfd/ .gnome2/
```
Then log out and back in.

---

### Post by pibbTibbs on 2009-07-16
Thanks for the quick reply!

That did something as now it gets to loading the black bar at the top, but now only shows the ubuntu icon on the far left, and the power, wireless and speaker icons to the right plus the time and date. Right click no longer brings up the options i mentioned in the previous post.

It's kind of like the desktop is now loading halfway and quits after initiating the wifi connection. Only things working now are through the tray icons. Cant get to anything else other than ctrl+alt+f2 for command line.

Thanks though, I almost think it's a good thing it did not run smooth "out of the box" as it gives me a good opportunity to learn.

J

---

