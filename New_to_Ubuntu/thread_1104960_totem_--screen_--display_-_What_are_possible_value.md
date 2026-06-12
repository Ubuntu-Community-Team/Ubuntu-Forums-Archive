---
title: "totem --screen --display - What are possible values?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by men28 on 2009-03-24
Hi!

I have tv connected to my computer and I can drag applications windows to it. But I am looking for possibility start totem in full screen mode on my tv. There are command line options --screen and --display.

What are possible values for those options?

---

### Post by Hospadar on 2009-03-24
How is it connected, seperate X screen, X screen with xinerama, twinview?
Depending on how it's configured, it may not be so easy.  Those arguments place the window on a separate X screen, but if you are using twinview (which is an nvidia thing, and nice for normal use) you may have issues.

Regardless, the values for the display argument is typically which xserver number,
:0.0 is the root (main) X server, I belive extras get added on like :n.0

Maybe doing an "xrandr -q" would help you determine which x screen is which.

---

### Post by men28 on 2009-03-24
I think displays are configured not very well.
This is one big screen with "TwinView".
nVidia video card.

```
$ xrandr -q
Screen 0: minimum 2944 x 1200, current 2944 x 1200, maximum 2944 x 1200
default connected 2944x1200+0+0 0mm x 0mm
   2944x1200      50.0* 

```

---

### Post by men28 on 2009-03-26
I didn't think so simple question has so difficult answer. I don't sure Absolute Beginner Talk forum is a right place for this thread.

I have read some interesting documentation:
[nVidia TwinView - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=1773584")
[HowTo: Dual Monitors (Xinerama/TwinView/MergedFB) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=221174&highlight=twinview")
[X(7) manual page]("http://www.x.org/archive/X11R6.8.0/doc/X.7.html")
[xorg.conf(5x) manual page]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html")

Then I started **nvidia-settings** utility and configured my TV and monitor as different X Screens.

There was a first problem. My tv was recognized as Monitor0 and when Ubuntu started a login screen was on the TV. This was not good!
I tried change "Screen 0" by "Screen 1" and vice versa, Monitor0 by Monitor1. It didn't help.
Only replace Screen0 by Screen1 in **ServerLayout** section resolved the problem:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen1" LeftOf "Screen0"
    Screen      1  "Screen0" 0 0
EndSection

```
I don't sure this was the best solution.

Then I tryed start Totem with **--screen** parameter and there were some strange errors about bug in the program. So I switched to **mplayer**.
This was much better. Now I can run commands like:
```
mplayer -display :0.1 -fs <my-video>
```
and see full screen video on my TV.

But now there is another problem.
When I swith to another user in my system there is only sound in mplayer and this error:
```

couldn't open the X11 display (:0.1)!
```

What's wrong?

---

### Post by taavikko on 2009-03-26
You can always open apps in other displays using "env" variables.

Example,
```
env DISPLAY=0:1 totem file.extensions
```

"xrandr" / "w" / "who" commmands gives you clues what are available displays.

The error in mplayer is that, that other user is using that display and it is reserved for him/her.

Anyways, man pages are always good to finding missing info on apps

---

### Post by men28 on 2009-03-27
This forum is a good place to look for ideas how to do things.

Command **who** returns something like:
```
$ who
user1    tty7         2009-03-24 22:14 (:0)
user1    pts/0        2009-03-27 05:24 (:0.0)
user2    pts/0        2009-03-27 05:24 (:20.0)

```

I have written a short script which processes this information for a current user and starts mplayer on my TV:
```
#!/bin/bash

d="`who | grep \`whoami\` | tail -1 | sed -r 's-^.+\(\:(.+)\).*-\1-' | awk -F\".\" '{print $1}'`"

mplayer -display :$d.1 -fs $1

```

And I have created launcher for this script on the desktop.
Now my wife can just drag and drop their videos on the TV icon.
Now it is not important which user was logged in first and where users are logged in on the system.

Thanks for help.

---

### Post by boyzonder on 2010-01-17
Hi, I have a dual monitor setup on an NVIDIA card, where one screen is a digital flat panel and the other analog TV. I wanted to accomplish something similar to what you did, which was to find a simple way to get MPlayer to play videos on the TV. I tried to use/adapt your script, but it doesn't do what is should in my setup and I can't figure out how what goes wrong.

Anyway, a much simpler solution to the same problem is the following. X stores an environment variable called DISPLAY, which looks like DISPLAY=:0.0 on the first display. Using shell (bash) string manipulation just extract the second character:
```
mplayer -display :${DISPLAY:1:1}.1
```
This yields 'mplayer -display :X.1' if DISPLAY=:X.0 such that it is quite flexible.

---

