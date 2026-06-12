---
title: "Rhythmbox missing files?"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-09-07
When I opened rhythmbox today I noticed it was giving me a message saying there were missing files. They were still on my computer obviously, but somehow rhythmbox lost them. They just disappeared from my playlists and library. I had to put them back, and for whatever reason it's refusing to re-accept some of them. I have no idea why, since I had them and played them just fine a few days ago. What could have caused this, and how can I avoid it in the future?

---

### Post by CFury on 2009-09-08
Did you by chance open these files originally from a flash drive or were they ripped from a CD?

---

### Post by Stebalien on 2009-09-08
My best guess is that rhythmbox's database has been corrupted if you don't care about your current playlists and settings, you can delete the contents of "~/.local/share/rhythmbox" and try rescanning your music folder. Also, try playing the songs that refuse to be added in another player such as totem (it comes with ubuntu). If the songs fail to play then they may have become corrupted and you should make sure that you hard drive is still healthy (using SMART etc...that is another topic).

---

