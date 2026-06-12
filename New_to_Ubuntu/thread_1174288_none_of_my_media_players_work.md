---
title: "none of my media players work"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by adamogardner on 2009-05-30
so when I double click a .flac for example the default movie player opens but doesn't play.  audacious, audacity, they can't play anything either.  What happened?

---

### Post by jimv on 2009-05-30
Try install the ubuntu-restricted-extras package.

---

### Post by adamogardner on 2009-05-30
> **jimv said:**
> Try install the ubuntu-restricted-extras package.

This did not work.  These things did work once.

---

### Post by jman5555 on 2009-05-30
Are you sure you have all of the proper codecs installed? (Under add/remove programs)

---

### Post by adamogardner on 2009-06-26
> **jman5555 said:**
> Are you sure you have all of the proper codecs installed? (Under add/remove programs)

no

---

### Post by mc4100 on 2009-06-26
Does it actually not start, no moving progress bars, etc., or does look as if it **is** playing only you can't hear anything?

---

### Post by carml on 2009-06-26
Try one of the players suggested here [HTML]http://ubuntuforums.org/showthread.php?t=240689[/HTML],if none of them works (just to check if  you have the correct codecs),then will try to find an other solution.

---

### Post by ~sHyLoCk~ on 2009-06-26
Install the proper gstreamer packages, also install flac

---

### Post by adamogardner on 2009-09-17
the progresss bar does not move.  the media player opens and doesn't start.

---

### Post by Bölvaður on 2009-09-17
> **adamogardner said:**
> the progresss bar does not move.  the media player opens and doesn't start.

It happened to me when I installed a special set of gstreamer plugins so I either needed to uninstall the wrong plugins and install the correct ones OR play everything through vlc.

open Add/Remove and look for flac, install the gstreamer plugin. You should also look for other gstreamer plugins but make sure when you install one it will not uninstall others... as some replace each other

---

