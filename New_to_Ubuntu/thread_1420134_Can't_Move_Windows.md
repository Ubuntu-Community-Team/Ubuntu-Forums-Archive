---
title: "Can't Move Windows"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by Prominence on 2010-03-02
Hi, I rarely ask for help, but I'm just...clueless in this case as to what to do.

This issue is happening on my desktop computer that's an AMD 64 bit, and whenever I log on, it looks as though there's something wrong with the window borders and I can't grip the windows to move them, however using ALT still works. 

At other times, it will work however, like it will glitch, then it may stop, it may glitch up again. My desktop computer is my work computer so I'd really like to have this issue resolved without reinstalling.

Also, whenever this issue happens, the computer tends to lag as a whole, which I can see via keyboard navigation. I have 7 GB of RAM, and a Quad Core Processor, and a Nvidia Graphics Card, so I don't know what could be causing the problem.

---

### Post by Temposs on 2010-03-02
Did you try disabling compiz and seeing if you still get the problem? It could be an issue with the graphics.

---

### Post by Prominence on 2010-03-02
> **Temposs said:**
> Did you try disabling compiz and seeing if you still get the problem? It could be an issue with the graphics.

Whenever I disable compiz, the window borders go with it

---

### Post by Temposs on 2010-03-02
Do you happen to be using Emerald window decorations?

---

### Post by Prominence on 2010-03-02
> **Temposs said:**
> Do you happen to be using Emerald window decorations?

No

---

### Post by Temposs on 2010-03-02
Can you go to System->Prefs->Appearance, and then select the Human theme. If that's already selected, then select Human-clearlooks. Then disable compiz and see if your window decorations remain.

---

### Post by Prominence on 2010-03-02
No window decorations, with any theme, already tried that a while back

---

### Post by asmoore82 on 2010-03-02
You could try to force re-install the compiz, metacity, and theme related packages.

Maybe before that you should create another desktop user account and log in
to see if the problem is system wide or just your userspace.

---

### Post by lyall on 2010-03-02
have you tried logging in using the **Failsafe Gnome** from the **Options** on the Login screen

it might be a place to start

good luck and have fun learning

---

### Post by darolu on 2010-03-03
Try installing the proprietary drivers; press ALT+F2 and then type "jockey-gtk", you should be able to install the proprietary drivers from there, it's very easy you shouldn't experience any problem.

Anyways, at any given time, if you find yourself without a windows manager (no borders, no bar to move windows) press ALT+F2 (or open a terminal) and type:
```
metacity &
```
This should fix the windows problem.

If you still experience lag after installing the proprietary drivers, -and considering you are running on a 4 cores processor with 7 GB of RAM and a Nvidia Graphics Card- you may want to run a memory test scan, as some of your RAM modules may be damaged.

You can check for resource-eating apps in a terminal with:
```
top
```

Press "Q" to exit, you can also see how much free memory you have:
```
free -m
```

---

### Post by giantclam on 2010-08-18
I am using Compiz Fusion with extra visual effects.  Once in a while when I start Lucid Lynx, the top windows borders are missing, so I can't move any windows around.  

I have discovered an extremely easy fix.  Install the "Compiz Fusion Icon", if you don't already have it installed.  Run it, and you will see it's icon in one of your panels.  Right click on the little icon and choose "Reload Windows Manager", and voila, everything is back to normal.

---

### Post by Zorgoth on 2010-08-18
The thing to do would be to make sure window decoration is set up right.

So emerald --replace

or 

gtk-window-decorator --replace

Make sure the compiz window decoration settings are set right.

Finally, you don't need a titlebar to move a window.  Just hold down <Alt> and drag.

---

