---
title: "Can't get flash movies to play in Firefox"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by skinks on 2010-02-12
I'm stuck.  I'm have been running Ubuntu 9.04 for about 5 months, and never have I been able to play flash content (swf files I believe) in my Firefox browser.  The content loads and then just sits there, usually with just a black screen.  Sometimes I get a box with gray "play" icon, but nothing happens.  The message at bottom of Firefox says Done but nothing is happening.

I've searched here for similar threads.  I've uninstalled, reinstalled Adobe Flash Plugin.  I've loaded copied libflashplayer.so file to /usr/lib/mozilla/plugins.  I've loaded the Ubuntu restricted formats.  Nothing works!  

I'm at a loss on what to try next.

---

### Post by skinks on 2010-02-12
Okay.  I fixed it.  The Swfdec player was installed as primary plugin for playing SWF.  I had to go to Synaptic Package Manager and uninstall it from there.  After that all is okay.

---

