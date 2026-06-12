---
title: "Mozilla firefox problems"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by greypatch on 2009-02-06
Whenever I open firefox it opens up in not full screen mode, but the top part that says for example right now "Ubuntu FOrums -POst New Thread- Mozilla firefox with the minmize and close buttons missing. the entire line is gone and I cant even see my taskbar. I have to right click into full screen and then go out of full screen again to bring it back to normal. ANy suggestions? I tried updating firefox but all I get is a tar.bz2 file and nothing happens. If anyone could help me A) Fix the missing top part of mozilla and B) help update, it would much be appreciated!

---

### Post by yeats on 2009-02-06
This is apparently a common problem - it happened on my wife's computer.  The solution, though, is fairly simple.  

Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=988570]("http://ubuntuforums.org/showthread.php?t=988570")

---

### Post by Spherical on 2009-02-06
you tried purging (yes, you sadly loose your plugins etc, backup your bookmarks if possible!)
then removing your ~/.mozilla/firefox dir (also remove from the root!)
If you don't use any other mozilla software (like thunderbird), just remove the entire ~/.mozilla directory.

Then re-install.

It's the only solution I can think of.

p.s.
Chris is faster and appearantly has an easier solution ;)

---

### Post by greypatch on 2009-02-06
alright guys thanks!

---

### Post by ChildOfMana on 2009-02-06
This happened to me too.

If you're using Compiz, install CompizConfig Settings Manager (if you haven't already);

```
sudo apt-get install ccsm
```

Open it and go to *Utility* (down the left-hand side), then select *Workarounds* and remove the tick from *Legacy Fullscreen Support*.

Should do the trick.

---

