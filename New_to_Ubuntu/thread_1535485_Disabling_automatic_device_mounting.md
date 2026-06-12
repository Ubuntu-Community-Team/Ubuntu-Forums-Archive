---
title: "Disabling automatic device mounting"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by SteelCore on 2010-07-20
I'm trying to figure out the best method to disable automatic mounting in Lucid (and Karmic). I found this [_post_]("http://ubuntuforums.org/showthread.php?t=13692") from 2006. I was wondering if it still applies as I can't risk breaking the system at this moment. Thank you.

---

### Post by mikewhatever on 2010-07-21
The automounting option is hidden in gconf-editor.
Open a terminal window and type 'gconf-editor', navigate to /apps/nautilus/preferences, and uncheck the 'media_automount' option.

---

