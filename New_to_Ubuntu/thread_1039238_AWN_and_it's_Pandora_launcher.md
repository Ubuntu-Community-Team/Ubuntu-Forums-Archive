---
title: "AWN and it's Pandora launcher"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by cartisdm on 2009-01-14
I'm using AWN 0.3.1 dock and the launcher thing for Pandora music player used to work great (by great it is basically a miniture browser that automatically launches pandora and plays music nicely tucked away).

Recently when I click the launcher it doesn't load the page correctly.  I get an error saying that page doesn't exist and "click here" to try Pandora's homepage instead.  Clicking to the homepage of course works and the launcher begins working as usual.

Why does it suddenly want to load some retarded page?  How can I change it to the correct homepage for Pandora.  I've already tried removing the icon and adding it back on which didn't do the trick

---

### Post by cartisdm on 2009-01-15
bump?

---

### Post by Vantrax on 2009-01-15
Try removing it from your panel and adding it again, and then check if there is a preferences option for it. Personally I don't user Pandora so im not sure how much help I can be. If that doesn't work try updating AWN, there might be a newer version of the launcher available from one of the launchpad repositories.

---

### Post by cartisdm on 2009-01-15
> **Vantrax said:**
> Try removing it from your panel and adding it again, and then check if there is a preferences option for it. Personally I don't user Pandora so im not sure how much help I can be. If that doesn't work try updating AWN, there might be a newer version of the launcher available from one of the launchpad repositories.

> I've already tried removing the icon and adding it back on which didn't do the trick

From what I can tell I have the newest version of AWN installed.  I also ran my usual updates, which should include any changes to AWN, and that doesn't change anything

---

### Post by psytrox on 2009-04-02
1...Search for "pandora.py" on your system.
2...Open with text editor.
3...Search for "pandora.com"
4...Remove junk after above address...(something about an .swf file.)
5...Works without manual redirection to Pandora's homepage.

Let me know if you have troubles.

---

