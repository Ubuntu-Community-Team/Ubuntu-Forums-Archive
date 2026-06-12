---
title: "How to auto-hide mouse cursor while typing?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2009-03-09
How to auto-hide mouse cursor while typing?

---

### Post by kanikilu on 2009-03-09
I don't know of a global way to set this, but certain applications may support it. For instance, a quick search brought up that this is possible to set in VIM.

...actually, I found this package called "unclutter" (in the repos) that supposedly does this. You can read about it here:

[http://times.debian.net/1097](http://times.debian.net/1097)

[http://packages.ubuntu.com/search?keywords=unclutter](http://packages.ubuntu.com/search?keywords=unclutter)

I've never used it though...

---

### Post by Mr_Bumpy on 2009-06-08
I don't think Unclutter hides the mouse pointer when typing, just when idle.

KDE4 apps hide the cursor while typing, which is nice, but that doesn't help those using Gnome apps, I'm afraid.

---

### Post by carlsmith on 2010-09-19
I tried unclutter and got it running in the background as a start up app, but it kept crashing. It only has one error message, 'someone created a sub-window to my sub-window! giving up', but I got it every time I opened an new window. Even if I just ran it manually on the command line, it still crashed.
I'm using wmii2 as the window manager, so this might be something to do with it, but unclutter doesn't work for me.

For the record, wmii2 is pretty good if you want that style of WM, but it takes some getting used to - be sure to read the intro on the website.

[Update]
I've played around with unclutter and got it working well enough, but it's still really brittle. I think a lot of it comes down to my own incompetency. I really don't fully understand exactly how X11 works.

If you want to try unclutter, do sudo apt-get install unclutter, then add the line:

unclutter -root -idle 2

to the end of .bashrc in Ubuntu 10.4. Change the 2 to the number of seconds you'd like unclutter to wait before it hides the cursor, I find 2 works fine. There is some way you can change the sensitivity for twitchy mouses if that's an issue, but I dunno how to do it.

---

### Post by killerblack on 2012-09-06
unclutter is very well but its does not work instantly in a web browser like it does inside a Linux application, it works instantly inside Linux app.

---

