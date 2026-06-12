---
title: "X forwarding with Cygwin"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Steve Smith on 2007-02-23
I've been using [XWinLogon](http://www.calcmaster.net/visual-c++/xwinlogon/) to do X forwarding over SSH, to give a gnome-session on WinXP.  That all worked fine, with a startup script of:

```

SET PATH=c:\Program Files\xwinlogon
SET DISPLAY=:0
start XWin_GL.exe :0 -clipboard -trayicon -bs -keyhook -nowinkill -nodecoration
start xterm -e /usr/X11R6/bin/ssh -Y username@hostname gnome-session

```

I uninstalled that and put Cygwin on, and haven't been able to get it to work.  I've tried various ways of starting X, but I'll just begin with one way, to keep this post short!  If I run startxwin.bat, I get a run.exe dialogue box:
```

Error: could not start d:\cygwin\bin\xterm.exe'' -e /usr/bin/bash -l

```

I took that line out of the script, so it just started X, and that works.  The system  tray icon says 0:0.

In Cywin I then do
```

ssh -Y username@hostname

```
and get a command prompt from the Ubuntu  server.  Running a graphical app (eg gedit) returns
```

cannot open display: (null)

```

There are suggestions online to manually set the display, but as I understand that's incorrect if you are doing X forwarding.

Any help would be appreciated!
Steve

---

### Post by Steve Smith on 2007-02-24
I've been using [XWinLogon](http://www.calcmaster.net/visual-c++/xwinlogon/) to do X forwarding over SSH, to give a gnome-session on WinXP.  That all worked fine, but now I've changed to Cygwin and can't get it to work.

I don't want to cross-post, but couldn't work out where it would get the most attention from people who know what they're talking about, so please see the thread in Networking for all the details, and reply there:

[http://ubuntuforums.org/showthread.php?t=368781](http://ubuntuforums.org/showthread.php?t=368781)

Thanks!

---

### Post by thenebcouk on 2007-02-26
If you just require X-Forwarding have a look at XMing:
[http://freedesktop.org/wiki/Xming](http://freedesktop.org/wiki/Xming)

It works very well from a windows platform and I use it all the time when stuck without a linux machine. It just *works* out of the box.

---

### Post by houstonbofh on 2007-02-26
I also recommend xming and putty.  One minute to setup a Win machine, and it just works.

---

### Post by houstonbofh on 2007-02-26
As said in your post in the server forum, I like xming and putty.  Very simple setup and they work out of the box.

---

### Post by Steve Smith on 2007-02-28
Please see my reply in other thread!

---

### Post by Steve Smith on 2007-02-28
Thanks for all the recommendations for xming on this and the other thread, but I had xwinlogon doing just that before.  My problem is that I specifically want it to work through Cygwin.

---

### Post by bapoumba on 2007-02-28
@ Steve Smith: threads merged. As you can see, it is quite uneasy to handle to separate threads ;)

---

### Post by Steve Smith on 2007-02-28
> **bapoumba said:**
> @ Steve Smith: threads merged. As you can see, it is quite uneasy to handle to separate threads ;)

Thank you!  lol.  I was rather hoping people would just reply in the original thread.  Judgement on me for being cheeky and trying to get extra exposure... :)

---

