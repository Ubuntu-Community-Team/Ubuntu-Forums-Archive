---
title: "Lost my Task Bar"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by nava2 on 2009-06-05
Some how, I have lost my taskbar on my second workspace.

It has the bottom one, but not the top.

I think it has something todo with Compiz, I installed it, messed it up because my graphics card stinks, and fixed it after.

Any one have any ideas? Helpful suggestions? 

*Sidenote* My WINE won't run any programs, ideas? */Sidenote*

---

### Post by nava2 on 2009-06-05
Not sure if bumping is allowed but.. bump..

---

### Post by bacardiandwatermelon on 2009-06-05
Right click->new panel?

---

### Post by nava2 on 2009-06-05
> **bacardiandwatermelon said:**
> Right click->new panel?
No such luck. :(

---

### Post by QIII on 2009-06-05
Try alt+f2 to open the terminal and type gnome-panel.

Let us know if that works.

(Oh.  And I think the moderators would prefer 24 hours before a bump.)

---

### Post by prvteprts on 2009-06-05
Only on the second workspace? What about the other workspaces? You could try decreasing your workspaces to just one, then add new ones after.

---

### Post by UbuntuNerd on 2009-06-05
can you right click on the panel you have and press "add to panel"

---

### Post by nava2 on 2009-06-06
> **QIII said:**
> Try alt+f2 to open the terminal and type gnome-panel.

Let us know if that works.

(Oh.  And I think the moderators would prefer 24 hours before a bump.)
That didn't work :( It ran, but nothing came of it. Still am missing the applications, places, system etc bar. =/

(Okay, thank you :))

---

### Post by knuthf on 2009-08-07
Yes - it is consistent - your taskbar is lost in the other workspaces, and has been introduced by some of the fixes released lately.
A simple remedy is probably to reinstall Ubuntu.

I have been playing around with the CompizConfig Manager, and there is little that helps. I managed to recover a lost workspace, and can now move applications, but there is no workspace, so it is impossible to launch in other workspaces. ALT+SHIFT+TAB does NOT work.

If you think you know what is wrong - do not just tell me to execute a command, but explain what the command does so we can learn what settings cause this. Please :-)

---

### Post by rasmusjenkins on 2009-08-21
This just happened to me, the item to add to the panel is 'Menu Bar'.  It worked for me, I just deleted panel and made a new one.  Hope this helps.

---

### Post by oboedad55 on 2009-08-21
> **rasmusjenkins said:**
> This just happened to me, the item to add to the panel is 'Menu Bar'.  It worked for me, I just deleted panel and made a new one.  Hope this helps.

mv $HOME/.gconf/apps/panel $HOME/.gconf/apps/panel-old 
sudo /etc/init.d/dbus restart

This will restore your panels to the default, like at the first install. I did this the other day and it worked perfectly.

Jon

---

