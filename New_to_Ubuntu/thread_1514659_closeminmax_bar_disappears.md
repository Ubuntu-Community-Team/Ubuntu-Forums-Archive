---
title: "close/min/max bar disappears"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by fatguy79 on 2010-06-21
My close/min/max bar keeps disappearing at least once a day. when it happens I close the window at all (even with force quit app). Has anyone else experienced this, or better yet, knows how to prevent it from happening.

---

### Post by Paqman on 2010-06-21
Next time it happens, try hitting Alt-F2 and running this command:
```
compiz --replace
```

If your window decorations come back, then Compiz must have died.

As an alternative to the command above, you could install the package [fusion-icon](apt:fusion-icon), which will put a little Compiz applet in your panel so you can restart Compiz with a mouse-click.

---

### Post by fatguy79 on 2010-07-05
didn't work

---

### Post by sansa90 on 2011-02-27
Bump for more options. Same thing is happening to me.

---

### Post by kroq-gar78 on 2011-02-27
maybe do
```
metacity --replace
```
instead of
```
compiz --replace
```?

---

