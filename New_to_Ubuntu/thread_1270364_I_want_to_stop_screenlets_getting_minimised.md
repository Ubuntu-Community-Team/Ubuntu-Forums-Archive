---
title: "I want to stop screenlets getting minimised"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Falc7 on 2009-09-19
I am trying to stop my screenlets getting minimised when i click the 'show the desktop' button in Kubuntu. I tried 'enabling widget layer' in compiz settings, but it didn't work.

Another solution was posted here:
[http://ubuntuforums.org/showthread.php?t=730162](http://ubuntuforums.org/showthread.php?t=730162)
----------------------------------
If you are using gconf then start gconf-editor and uncheck this value:

/apps/compiz/general/allscreens/options/hide_skip_taskbar_windows

No need to set "Treat as widget" in the screenlet and no need to enable "Widget Layer" in compizConfig. Screenlets will no longer be minimized along with other windows. Worked like a charm for me anyway.
------------------------------------

But would this work, as i'm using KDE not gnome?
If not, how can i stop them getting minimised?

---

### Post by CaptainMark on 2009-09-19
does compiz work differently in kubuntu? i dont know but i had the same trouble in ubuntu and in compiz in the general options at the top the general tab has the options of hide skip taskbar windows, tick it, then with every screenlet you want permanently stuck to the desktop right click it and go to properties and on the options tab you tick the skip taskbar option, hey presto. 
I think this is just a more GUI based method of doing what youve quoted from another post.

---

### Post by Falc7 on 2009-09-19
Both of those boxes were already ticked :p Still don't work

---

### Post by CaptainMark on 2009-09-19
ah that stumps me, try in the window rules plugin, non minimisable windows and click the ones you need to add, i tried this first but for me this didnt work and the other method did

---

### Post by Falc7 on 2009-09-19
That didn't work either :(

---

