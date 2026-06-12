---
title: "Delete all Banshee settings?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-11-22
Hi

My Banshee install has gone a bit haywire and doesnt sync my mp3 player any more - I want to uninstall it and remove all settings in the hope that reinstalling it sets it back to defaults.

However even if I do a complete removal uninstall, when I reinstall it still points to my media library (which isnt in decault location) so my previous settings (and problems) still exist.

How can I delete all settings and restore to default?

Cheers

---

### Post by RedSingularity on 2009-11-22
Try this in a terminal

sudo find / -name banshee

That will give you all the files with the name banshee.  Then you can delete them.

---

### Post by antony.s on 2009-11-22
Banshee probably stores its settings in a hidden (. folder) in your home directory called ".banshee"

In terminal try

cd ~/.banshee

If that works then

rm -rf ~/.banshee

---

### Post by aquascrotum on 2009-11-22
Neither method turned up anything unfortunately...

---

### Post by ajgreeny on 2009-11-22
Try ```
locate -i banshee
``` to find all files named banshee, but ignoring letter case, just in case it really does have files or folders called Banshee.

---

