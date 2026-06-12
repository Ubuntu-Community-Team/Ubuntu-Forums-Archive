---
title: "No menus / no functions"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by ghostrayne on 2011-05-19
I'm new to linux, just 3 days in now. I love it! However, twice now i've gotten myself in this prediciment. Im running Ubuntu 11.04 off of my hard drive. I whiped it clean and freshly installed. The problem that I've ran into (for the second time) is the disappearance of my menus.  When editing settings in compiz manager, my top menu bar glitches out. That's fine though because I can still click where the buttons would be if i could see them. And that only lasts until I reload it or relogin. However, when I turned something off - I gotta mega glitch. The top bar completely disapeared and the quickstart menu (on the left) also dissapeaered. Ican see my wallpaper, and I can right click and have the regular menu pop up there. I tried restarting, but it just loads up the desktop. I am currently logged in with "ubuntu classic mode" - ubuntu <--- non classic mode, is the one i'm having a problem with. 

The first time - I searched around, couldnt really find anything (this whole thing is like an alternate language to me atm as its only day 3), so i just reinstalled the OS again. 

All was fine until an hour ago - somehow, i did it again. 

I've searched again. I cannot open things with keyboard shortcuts or functions. ALT F2 does nothing. I can open up the terminal with CTRL+ALT+F1. But the commands that i've seen as answers to other peoples issues don't work. Most commonly the "gnome - " commands and the "xhost" commands just return "Unable to load display" 

I figure if I could possibly reset the startup configuration that might solve the issue, but i can't find it. The directory that most people have suggested (in similar problems) is not where mine is. Could be that these issues were surfaced at a much older version of Ubuntu. 

Anyways, anyhelp is GReATLY appreciated. And thank you for sitting through this horrible grammar, horrible spelling, horrible written query. I have been working pretty hard for the last 8 hours straight, and I just don't feel like actually "trying" to type any more. Thank you.

---

### Post by Mr. Shannon on 2011-05-19
I don't use Unity so I'am only guessing here, but, have you installed any proprietary drivers for your video card?  Compiz relies upon the graphics card.  To install proprietary drivers in Ubuntu (classic) click on **System->Administration->Additional Drivers** then use the window to activate a graphics driver (try recommended first if it exists).  If there are no drivers in that window then you can't (easily) install proprietary drivers.

If the above method does not work then hopefully someone who uses Unity will chime in.

---

### Post by ghostrayne on 2011-05-19
Problem is i can only see my wall paper and can't click anything... I can run the terminal. That's all i can do. lol

---

### Post by ghostrayne on 2011-05-19
ooh wait, in classic?So ... if i install these things on classic then nonclassic will go back to normal?

---

### Post by ghostrayne on 2011-05-19
Didn't work - there was nothing in the list.

---

### Post by Mr. Shannon on 2011-05-19
Did you change Compiz to use the desktop cube in unity?  If you did then that could be the problem. In that case see this thread: [http://ubuntuforums.org/showthread.php?t=1762865]("http://ubuntuforums.org/showthread.php?t=1762865")

---

### Post by wildmanne39 on 2011-05-19
> **ghostrayne said:**
> I'm new to linux, just 3 days in now. I love it! However, twice now i've gotten myself in this prediciment. Im running Ubuntu 11.04 off of my hard drive. I whiped it clean and freshly installed. The problem that I've ran into (for the second time) is the disappearance of my menus.  When editing settings in compiz manager, my top menu bar glitches out. That's fine though because I can still click where the buttons would be if i could see them. And that only lasts until I reload it or relogin. However, when I turned something off - I gotta mega glitch. The top bar completely disapeared and the quickstart menu (on the left) also dissapeaered. Ican see my wallpaper, and I can right click and have the regular menu pop up there. I tried restarting, but it just loads up the desktop. I am currently logged in with "ubuntu classic mode" - ubuntu <--- non classic mode, is the one i'm having a problem with. 

The first time - I searched around, couldnt really find anything (this whole thing is like an alternate language to me atm as its only day 3), so i just reinstalled the OS again. 

All was fine until an hour ago - somehow, i did it again. 

I've searched again. I cannot open things with keyboard shortcuts or functions. ALT F2 does nothing. I can open up the terminal with CTRL+ALT+F1. But the commands that i've seen as answers to other peoples issues don't work. Most commonly the "gnome - " commands and the "xhost" commands just return "Unable to load display" 

I figure if I could possibly reset the startup configuration that might solve the issue, but i can't find it. The directory that most people have suggested (in similar problems) is not where mine is. Could be that these issues were surfaced at a much older version of Ubuntu. 

Anyways, anyhelp is GReATLY appreciated. And thank you for sitting through this horrible grammar, horrible spelling, horrible written query. I have been working pretty hard for the last 8 hours straight, and I just don't feel like actually "trying" to type any more. Thank you.
Hi, you disabled the unity plug-in, below this text in my signature it say restore unity and compiz, if you restore unity that will fix your problem.

---

### Post by ghostrayne on 2011-05-20
Thank you Mr.Shannon - What you suggested wasn't the correct fix for my  issue, but I still heavily thank you for your time and effort. 

Wildmanne - What you suggested was exactly the problem I was having. I feel unworthy of linux atm for how simple that was. I don't understand why the others that were getting such similar symptoms had fixes that were completely unrelated to this fix. Resetting Unity solved my issue immediately. Thank you for your time and your simple guide. You're a life saver.

---

