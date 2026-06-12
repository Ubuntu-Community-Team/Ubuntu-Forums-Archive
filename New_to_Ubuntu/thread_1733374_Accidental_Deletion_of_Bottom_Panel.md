---
title: "Accidental Deletion of Bottom Panel"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Inhopeless on 2011-04-19
I was running 10.10 under 'Ubuntu Classic' mode, because I like the bottom toolbar, and I like the sidebar thing. 

I wanted to delete a little applet that I put in the wrong place on the bottom toolbar. A message pops up saying something about losing data. Unbeknown to me, instead of deleting the applet, I deleted the entire toolbar.

I've tried ALT+F2 'gnome-panel' and restarted, but that just got me back to where I was in the beginning.

So, how do I get it back? Any ways possible, GUI, terminal etc.

---

### Post by SwimDude0614 on 2011-04-19
You should be able to right-click on your top-panel and choose "new panel". When I tried that, one popped up at the bottom of my screen (I've deleted the bottom one on purpose - don't like it). If yours pops up somewhere else, simply right-click it where ever it appears and choose "Properties" and adjust the "Orientation" to bottom. At that point, it will take some experimenting to see exactly which items it is in the list that you need to add back in there - but they are all there.

Since you've already deleted it, you might enjoy my setup. I have the top bar as it came from the distro (10.04) with the addition of the window switcher. Then at the bottom of my screen, I have Cairo Dock, which is similar to Apple's dock application, and very customizable.

Cheers!
David

---

### Post by Inhopeless on 2011-04-19
Whoops, I'm running 11.04, sorry. In any case, that didn't work.

---

### Post by ~Plue on 2011-04-19
run the following from a terminal/run dialog
```

gconftool-2 --recursive-unset /apps/panel
[LEFT]rm -rf ~/.gconf/apps/panel[/LEFT]
killall gnome-panel
```that should reset the panels to the default

---

### Post by Inhopeless on 2011-04-20
Thank you! It worked like a charm!

---

### Post by dcsoldschool53 on 2011-04-20
Don't for get to mark the thread as solved.

---

