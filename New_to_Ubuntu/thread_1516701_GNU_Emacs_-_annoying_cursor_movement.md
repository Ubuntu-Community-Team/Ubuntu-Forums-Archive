---
title: "GNU Emacs - annoying cursor movement"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by khantastic on 2010-06-24
Hello

My apologies if this is not the correct place for this thread.

Using GNU Emacs 23.1.50.1, available in Ubuntu 9.10, the cursor move in an annoying way. It jumps one character backwards when moving the cursor one line up or down, but only if I edited the line I'm moving from.

E.g. if I have two lines with text and cursor is standing at pos 1 on line 1 (x,y) = (1,1). If I then insert a space such that cursor is located at (2,1) and move one line down I would expect it to be located at (2,2), but this is not the case. It ends up in (1,2).

This is really annoying. Anyone knows how to configure this? I haven't seen this on previous versions of Emacs available in Ubuntu.

Thanks in advance.


SA

---

### Post by Sef on 2010-06-25
Moved to Absolute Beginners.

---

### Post by khantastic on 2010-08-04
I found out whats causing this annoying cursor movement. When shift+leftclick you can increase or decrease text size. The annoying movement occurs only when decreasing the text size.

---

