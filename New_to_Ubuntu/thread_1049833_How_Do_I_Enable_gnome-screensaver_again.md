---
title: "How Do I Enable gnome-screensaver again?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Teasdale on 2009-01-25
I wanted to try xscreensaver, so I installed it with synaptic package manager. When I opened it, it wanted me to disable gnome-screensaver, so I did. But xscreensaver wouldn't lock my screen, even though that option was checked. So I uninstalled it with synaptic package manager.

Now gnome-screensaver doesn't work. I guess I need to re-enable it, or the daemon, or whatever xscreensaver turned off. How do I do that? I tried reinstalling gnome-screensaver with synaptic package manager, but that didn't help.

-----------------

I tried uninstalling gnome-screensaver, restarting the computer, and then installing gnome-screensaver again. That still didn't enable it.

-----------------

Now I've installed xscreensaver agin. When I open it says, "The XScreenSaver daemon doesn't seem to be running on display ":0.0".  Launch it now?" So I clicked okay. It locks my screen if I manually open xscreensaver and click "lock screen now." But I really need what I had - for the screensaver to come on automatically after the computer has been idle. Xscreensaver's isn't working, and gnome-screensaver/lock screen is disabled.

------------------

OK, so, looking through the xscreensaver options, I can manually lock the screen and start the screensaver. I can choose how long the screensaver will run, and when to lock the screen. But I don't see any way to tell it to start the screensaver and lock the screen after the computer has been idle for so many minutes, and that's what I need to do. So, I think i need gnome-screensaver back. 

How do I get gnome-screensaver back?

---

### Post by whoop on 2009-01-25
To lock the screen you can also hit Ctrl+Alt+l. This will lock the screen immediately.

---

### Post by Teasdale on 2009-01-25
But I want it to lock when I'm away and forget to manually lock the screen.

---

### Post by Teasdale on 2009-01-25
It's beginning to look like a new, clean install of Ubuntu is the only possible fix. From my google searches, nobody seems to have ever run into this. 

One would think that this would have been a minor problem with a simple terminal command to fix it.

---

### Post by Teasdale on 2009-01-25
Someone suggested locating instructions to use xscreensaver instead of gnome-screensaver, but to do it backwards.

I found this:
[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)
but that's from 2006, and not for the version of Ubuntu I'm running. Even step 1 isn't relevant to Ubuntu 8.04: "To configure gnome-screensaver not to function, go to System / Preferences / Screensaver and uncheck both checkboxes;"  When I go to System / Preferences / Screensaver there aren't any boxes to check, only drop-down options to change the item on the panel.

But might that thread show some kind of a clue as to how to revert back to gnome-screensaver?

---

### Post by whoop on 2009-01-25
how did you disable gnome-screensaver?

---

### Post by Teasdale on 2009-01-26
When I opened xscreensaver, a pop-up box came up and asked me something - twice; each pop-up box asked something different. I don't remember the exact wording, but one said that gnome-screensaver was already running and needed to *not* be running in order for xscreensaver to be able to work. So I clicked the box to allow xscreensaver to make gnome-screensaver not run. I didn't think it would be difficult to un-do.

When I uninstalled xscreensaver to see if that would fix it, and then reinstalled it to see if that pop-up box would come up, one of those pop-up boxes came up again when I opened xscreensaver, but it wasn't the one having to do with gnome-screensaver.

---

### Post by Sean_b84 on 2009-01-29
> **whoop said:**
> how did you disable gnome-screensaver?
i've found the easiest way to get rid of it is 
"sudo apt-get remove gnome-screensaver"

---

### Post by Teasdale on 2009-01-29
Here's something interesting - Ubuntu just updated and I had to restart the PC. And gnome-screensaver is working! It appears that the update disabled xscreensaver. :confused:

---

