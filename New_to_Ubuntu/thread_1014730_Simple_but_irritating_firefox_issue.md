---
title: "Simple but irritating firefox issue"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by victorcrane on 2008-12-18
Hey folks, after several months of learning I finally have my system running exactly as I'd like it to, aside from one thing...

Every time I start firefox, the first time during that session that I try to access the bookmarks list, rather than dropping the list down, it simply bookmarks whatever site I'm looking at at the time. This seems like nothing really, and it's hardly the most troublesome thing in the world, but it means I continually have to empty all the erroneous rubbish from my bookmarks list. Has anyone encountered this before and is there any way to stop it from happening?

It's annoying the hell out of me. 

I'm running intrepid on a hopeless dell inspiron 1300 laptop. I'm glad I didn't pay for it, I've seen shoes with more processing power than this...

:guitar:

---

### Post by bryncoles on 2008-12-18
cant help you with your firefox issue, except to say i have found the 'fox buggy since 8:4 - Heron. i find right clicking to have nothing but random effects!

but, if you're system is slow, have you considered xubuntu?

see the minumum spec?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[http://www.buildyourown.org.uk/pc-installing/ubuntu/](http://www.buildyourown.org.uk/pc-installing/ubuntu/)

and heres a guide to swapping the standard ubuntu for xubuntu

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by phantomjoker on 2008-12-18
have the same problem - and if it is the same problem, then clicking the bookmarks tab by holding down the mouse button for a while before releasing it should help.

What happens is firefox sees the very fast click as 2 clicks (god knows why) and if you look, the top selection in the menu is 'bookmark this page' so that's what it does....

try that..

---

### Post by sarwiz on 2008-12-18
I've had these same problems using firefox in windows since 2.0.2, the add bookmarks section got all buggy and sometimes doesn't work at all. Using ff in 8.04 seems to work fine, but still cannot expand the add bookmark box.

---

### Post by Stefanie on 2008-12-18
you can use the keyboard shortcut alt+b to open the bookmarks menu.

---

### Post by philinux on 2008-12-18
Simple fix for this. Get your bookmarks sorted. Then back them up using organise bookmarks or copy the bookmarks.html file somewhere safe.

Then delete the .mozilla folder. Fire up firefox and copy back your bookmarks. Or use the profile manager to create a new profile.
[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

---

### Post by clive littlewood on 2008-12-18
Hi

I had the same issue but after todays updates it has cleared !!!!!   :p


Clive   ):P

---

### Post by victorcrane on 2008-12-19
Hey guys, some handy tips there many thanks, it's great to know it isn't just me. I shall look into this xubuntu business asap. 

Have a great xmas all! 

:guitar:

---

### Post by FuturePilot on 2008-12-19
This bug [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313")

---

### Post by cb951303 on 2008-12-19
> **clive littlewood said:**
> Hi

I had the same issue but after todays updates it has cleared !!!!!   :p


Clive   ):P

From mozilla's bugzilla it looks like it's assigned to someone 2 days ago and it's not flagged as done yet. I think the bug may persist.

---

### Post by bryncoles on 2008-12-19
i installed xubuntu on my old desktop pc at home the weekend gone - it was previously dual-booting gutsy gibbon and windows ME (of all things!). it could just cope with gutsy, but xubuntu ibex runs like a dream on it. 

im so impressed with xubuntu, im considering defecting to it full-time!

---

### Post by flanagan on 2008-12-19
This problem seems to be related to how the various browsers handle mouse events. Perhaps they changed how Firefox handles the right click event in recent versions.

It sure is annoying and easy to reproduce. Firefox launches a menu item on  mouseup of the right button. This seems like desired behavior for the left button (or the button that you would normally use to launch a pop-up menu item), but not for the right button (or the button used to get a context menu). To reproduce the problem, just have your mouse traveling southeast across a link as you right-click it. Eventually you will do this fast enough so that the mouseup event happens while the pointer has traveled into the popup menu, launching something undesired.

You can see this happening slowly by right-clicking a link and dragging into the menu while the button is down. Whatever item you are on when you release the right button gets launched. Same problem for menu bar items in Firefox.

Same behavior in Epiphany and Konqueror.

It does not happen in Opera since context menus only pop up when you release the button. Menu bar dropdowns don't come up at all with a right-click. This seems like correct behavior to me. 

This is not enough of a problem to get me to use Opera on a regular basis, but in my mind, this continues a disturbing trend of Mozilla making changes or ill-thought design decisions without adequate testing (e.g. release of 3.0.4 with buggy/lagging Flash functionality, and, before that, making the awful/awesome bar the default).

---

### Post by cb951303 on 2008-12-20
> **cb951303 said:**
> From mozilla's bugzilla it looks like it's assigned to someone 2 days ago and it's not flagged as done yet. I think the bug may persist.


Confirmed. the bug is still there

---

