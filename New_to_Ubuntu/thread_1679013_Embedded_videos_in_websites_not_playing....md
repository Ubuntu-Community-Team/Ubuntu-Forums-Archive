---
title: "Embedded videos in websites not playing..."
date: 2011-01-31
forum: New to Ubuntu
---

### Post by gatorbrit on 2011-01-31
Hi, I created some screencasts - both avi and mpeg4 and put them on a class website for my students.  I was able to view them on my desktop without any issues.

Now when I go to the website, I get told that I need a plugin and also that it is looking for a text/html plugin.

This happens for both chrome and firefox.

I can view the videos just fine in windows though.   Any suggestions?

---

### Post by SeijiSensei on 2011-01-31
Try installing [gecko-mediaplayer](http://packages.ubuntu.com/lucid/gecko-mediaplayer) from the repositories and see if that helps.

I don't think you'll need to install ubuntu-restricted-extras to watch videos you've created in those formats.  Those typically concern proprietary items like mp3 and DVD playback.  Can't hurt, though.

---

### Post by gatorbrit on 2011-01-31
> **SeijiSensei said:**
> Try installing [gecko-mediaplayer](http://packages.ubuntu.com/lucid/gecko-mediaplayer) from the repositories and see if that helps.

I don't think you'll need to install ubuntu-restricted-extras to watch videos you've created in those formats.  Those typically concern proprietary items like mp3 and DVD playback.  Can't hurt, though.

That worked - partly.  It plays fine now in firefox, but not in Chrome.  I am pretty sure that it is because Chrome is not using the right plugin.  I wonder how I can get chrome to use gecko to open the file?

---

### Post by PunkLV on 2011-01-31
Check the Firefox and Chrome plugin paths. 
Go to page:
```
about:plugins
``` for Firefox, and something similar in Chrome (had never used it)
There check the corresponding gecko-plugin paths and edit as necessary.

---

### Post by gatorbrit on 2011-01-31
> **PunkLV said:**
> Check the Firefox and Chrome plugin paths. 
Go to page:
```
about:plugins
``` for Firefox, and something similar in Chrome (had never used it)
There check the corresponding gecko-plugin paths and edit as necessary.

I'll have to do some work on this  - I can view the plugins, but it is not clear at all how to change them in chrome.

I did however install "Chromium" and it works great in that.  All very puzzling.  But I think I'll mark this as solved.  It seems to be an issue with my chrome installation.

---

