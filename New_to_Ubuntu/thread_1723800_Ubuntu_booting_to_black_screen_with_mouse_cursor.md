---
title: "Ubuntu booting to black screen with mouse cursor"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by xpapax on 2011-04-07
I had some problems getting my system to boot the other day.  I was getting errors so I googled them to see what I could find.  I ended up apt-get removing a bunch of stuff and reinstalling it.  In the end it turned out the problem was that my partition was full.  I cleared some stuff out but now I cannot get it to start correctly anymore.  When I start the machine up the screen stay blank with a blinking white cursor in the top right corner, and after a couple seconds the monitor goes into stand by.  So i restart and get to the screen where I can select "recovery mode". I select the recovery mode option on the next menu I pick continue with normal start.  It brings me to the command line, and if i try startx from here the monitor doesnt turn off this time, but a flash of random colors then I get a black screen with a white mouse cursor that i can move around.  I can still do ctrl alt F1 and get back to the command prompt.

The command prompt shows
> Current version of pixman: 0.18.4
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Markers....
...
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr....
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] Kernal modesetting enabled


this is where it stops, there is just a blinking cursor.


Does anyone have an idea as to what I can do to try and recover from this?  Would a fresh install be the best bet?  Also is there any output or files that I could post that could help shed some light on the problem?

---

### Post by chrisod on 2011-04-07
It sounds like you might have accidentally deleted something important when you "cleared stuff out". Is your home directory in a separate partition? If so, I'd just reinstall since you can do so without losing anything important. If not, maybe worth trying to work around a bit more first.

Another idea - unlikely to work but worth trying. Select an older kernel image from the grub boot screen. Unless of course you just deleted all your old kernel images when you were making space.

---

### Post by xpapax on 2011-04-07
All the files are in the same partition unfortunately.  When i say > I cleared some stuff out it wasn't just randomly targeted stuff, I only removed stuff I knew wasn't important.  How do I select a different version of the kernal?

---

