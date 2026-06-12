---
title: "Where  do screenshots go?"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Paper Pusher on 2011-02-13
I just installed Ubuntu 10.10 DTE-64 on a computer and I'm having a hard time taking screen shots.

I've tried both alt+PrintScreen and Applications>Accessories>Take Screenshot.

The documentation says that a Save dialog should appear after I take a shot, but no such dialog appears in either case.

I have looked through my home folder, but couldn't find it.  I tried to paste it into Open Office, but there was nothing to paste.

Help!

---

### Post by grahammechanical on 2011-02-14
I am using 10.10 64bit. In my case the screenshots are put on the desktop and I can move them from there to any folder I like.

I do get the Save screenshot dialog box with the option to select the destination and also to save to clip board.

Once I have used the application pressing Print Screen is enough to get a screen shot with the save dialog.

I have just tested this, so I know it works. Why is it not working for you? I haven't a clue.

Regards.

---

### Post by mcduck on 2011-02-14
> **Paper Pusher said:**
> 
I've tried both alt+PrintScreen and Applications>Accessories>Take Screenshot.

Try just the PrintScreen, without Alt.

Also if you have visual effects enabled, install CompizConfig Settings Manager (if you haven't got it already), and then make sure you have the "Gnome Compatibility"-plugin enabled, and in it's settings the command for screenshot set to "gnome-screenshot" & the command for Window screenshot set to "gnome-screenshot --window". Depending on your keyboard layout you might also have to change the keyboard shortcut fr a window screenshot into something else than Alt+PrtScr (at least for me it faisl to work with alt, so I set it to Shift+PrtScr instead).

If everything else fails, open a terminal and try running "gnome-screenshot". Post any error messages here.

---

### Post by Paper Pusher on 2011-02-15
Thank you all for your help and suggestions.  After some experimentation, I think I know what's going on.

Take Screenshot 
Grab the current window 

requires a delay of several seconds.
I had left the delay at the default of 0 seconds.

The other 2 options, whole desktop and select area, require no delay.

The delay requirement for window grabs is not documented in either the documentation or the user interface.  I had thought that it would use the last window selected prior to pressing the Take Screenshot button.  My mistake.  Take Screenshot silently takes no screenshot at all.

---

