---
title: "Guild Wars/WINE"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Pwhdavey on 2009-11-22
According to WINEhq Guild Wars runs fine. It did on Windows for me. I just got Ubuntu today after a year break, downloaded Guild Wars client, installed WINE. When I run the program through WINE (internet connected) it seems to be at something like.. 1fps. It doesn't load the main menu, it just loads the opening graphic very slowly. Have I done all the correct procedures? I'm on 9.10 by the way, not 7.10 like my avatar says.

---

### Post by undecim on 2009-11-22
Did you install WINE from the repositories (apt-get, software center, etc.), or by the instructions from winehq.org?

---

### Post by Pwhdavey on 2009-11-23
From the Software Centre.

---

### Post by undecim on 2009-11-23
Try installing it with the directions from winehq. I think it gives you a newer version

---

### Post by carniola on 2009-11-23
There's a long discussion of this bug [_here_]("http://bugs.winehq.org/show_bug.cgi?id=9263"). It includes a few suggestions for a fix, including [_this one_]("http://bugs.winehq.org/show_bug.cgi?id=9263#c44"):

```
* Uncheck "Allow pixel shader" in winecfg Graphics tab
* Start GW.
  in terminal: WINEDEBUG=-all wine Gw.exe
(the WINEDEBUG thing is to prevent wine from spewing loads of debug messages that, at least for me, interfered with GW rendering)
* Before logging in to ArenaNet, hit the Auto button at the bottom of the
Graphics tab in the Options window
* Whenever the frame rate drops (happens to me occasionally) just hit that Auto button again...
```

That may be worth a try? Good luck.

---

### Post by Pwhdavey on 2009-11-23
Thanks. When I type in that command in Terminal, it says it could not load/module not found. And I downloaded wine from winehq but it said it's already installed. In terminal, do I need to type something to authorise myself?

---

### Post by Pwhdavey on 2009-11-23
Okay when I opened GW from Applications>WINE>Programmes>Guild Wars>Guild Wars..GW didn't even appear. But the screen resolution changed so its all enlarged and slightly blurry. Just like game resolution, but the game isn't running visibly and is not on the taskbar either.

---

### Post by Annigma on 2010-01-22
Hi,

Did you get it sorted?
Did you try fiddling with settings in 'Configure Wine' (e.g. changing 'Windows version')?

Mine came up beautifully, but had no 'visible' place to log in, etc.. I changed the windows version to Win98 and it looks great. Sound's gone now though so I'm trying to figure that out hehe

Good luck
:D

---

