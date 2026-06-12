---
title: "xkill destroyed my Unity menu...how do I get it back?!"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by CajunPirate on 2011-07-03
I used xkill on the program's icon located on the Unity sidebar. Unsurprisingly (now), xkill killed Unity. Now I have a blank desktop with very limited controls. 

I cannot access my terminal through the shortcut "ctrl-alt-t." 
Rebooting did nothing.
The top menu is gone as well.
I could only access Chromium and post this by rightclicking and creating a html file...help?

How can I undo this?
Cheers!

---

### Post by createdcreature on 2011-07-03
Reinstall.:(

---

### Post by Bucky Ball on 2011-07-03
> **Robert Moyse said:**
> Reinstall.:(

Wouldn't go that far ... yet. At login, can you choose 'Ubuntu Classic' from the 'Sessions' menu? Does that give you regular 'classic' Gnome desktop?

---

### Post by CajunPirate on 2011-07-03
I had thought of that, but the option is gone from the login screen...

---

### Post by Bucky Ball on 2011-07-03
Can you boot in using the recovery kernel. At the end of that you will be hit with some options. Try 'Failsafe X'. Any luck?

---

### Post by Bucky Ball on 2011-07-03
Also, from here:

[http://www.reddit.com/r/IAmA/comments/en0ti/i_am_an_ubuntu_unity_developer_ama/](http://www.reddit.com/r/IAmA/comments/en0ti/i_am_an_ubuntu_unity_developer_ama/)
```

[LIST=1]
[*]Yes unity is going to be a plugin for compiz (is in fact), perhaps several
[*]You may disable it with CCSM, but that will leave you without panels if you dont launcher something else.
[*]You cant really xkill unity, its part of the compiz process. We try  to make all our helper processes failure/crash/kill resistant however :)
[/LIST]

```So, if Unity is a Compiz plugin ... the plot thickens. Why would that effect Gnome and where did that option go at login? Try the 'recovery' option and see if that gets you to a workable desktop ...

Also at the recovery options window you can choose to drop to a cli to fix the problem (a terminal). Try choosing that and typing 'startx'. If you drop to a root shell to do this and are successful in getting to a desktop, **BE** **CAREFUL** as you are logged into your system as root! Everything you do will count!

---

### Post by wildmanne39 on 2011-07-03
Hi, click on reset unity and compiz in my signature and just reset unity, this may not be possible if you can not use alt+f2 or ctrl+alt+t, I have help a lot of people reset unity, but I have never seen one broken by the kill command before, but unity is just a plugin in compiz.

---

### Post by CajunPirate on 2011-07-03
It happened right after I had installed 11.4, so there wasn't an older kernel to reload. I got your latest posts a tad to late, I went ahead and re-installed. Lesson here: xkill is one hell of a tool!
Thanks for the responses!
Cheers!

---

### Post by Bucky Ball on 2011-07-03
Good news and good luck with Ubuntu, CajunPirate. Please mark thread 'Solved' from 'thread tools', top right. ;)

---

