---
title: "A questions about fonts for anyone using Opera in Ubuntu..."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-12-04
I noticed that in the white text boxes on forums such as this used to input text for a post, the font is very light.  I think it may be normal and I just didn't notice it until now, but I just want to make sure this isn't some sort of glitch or whatever.  In FF the colours are solid and dark, it's just in Opera.

---

### Post by Space-Wolf on 2009-12-04
bump.

---

### Post by dca on 2009-12-04
I could've sworn Opera was written in Qt (a'la KDE) so you can install/use 'qtconfig-qt4' or depending on what version it's rendered in (qtconfig-qt3)...  Also, I think in the update from KDE3 to 4 that some of the locations have changed to where font config for all KDE apps you have installed on GNOME Ubuntu are kept - someone who's more adept and runs quite a bit of KDE/Qt apps on GNOME Ubuntu would better answer that question. You can type in *opera:config* in address bar and see if it references font types there.  Don't know if the below thread helps either.
 
[http://ubuntuforums.org/showthread.php?t=837528](http://ubuntuforums.org/showthread.php?t=837528)
 
 
...also try searching Ubuntu forums with your specific criteria because you may be right, it may be a glitch that shows up when using a non-aliased or hinted font...

---

### Post by Space-Wolf on 2009-12-04
Alright I fixed it.  You were right to suggest the opera:configure thing.  I went there and under fonts changed "Form.text" to Times New Roman from Courier and it looks a lot better.  So if anyone else is having this problem, just change the font in opera:config.

---

