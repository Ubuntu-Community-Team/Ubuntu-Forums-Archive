---
title: "[SOLVED] resizing xboard"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by minsf on 2008-12-23
i have the same problem as in this thread:
[http://ubuntuforums.org/showthread.php?t=234585&highlight=xboard+resize]("http://ubuntuforums.org/showthread.php?t=234585&highlight=xboard+resize")
anyone knows how to force resizing of a gdm window? maybe from the cli?
Edit: and just like him, the resize option is greyed out (when you right click on the top of the window) and the alt+f8 doesnt work.

---

### Post by jimmy the saint on 2008-12-23
you could ALT-CLICK anywhere on the window to drag it around and expose the bottom ritht corner.  From there you should be able to resize.

---

### Post by albinootje on 2008-12-23
> **minsf said:**
> i have the same problem as in this thread:
[http://ubuntuforums.org/showthread.php?t=234585&highlight=xboard+resize]("http://ubuntuforums.org/showthread.php?t=234585&highlight=xboard+resize")
anyone knows how to force resizing of a gdm window? maybe from the cli?

In a terminal :
```

xboard -size medium

```
And if you're feeling bored, try the mind-boggling :
```

man xboard
xboard -h

```
:)

---

### Post by minsf on 2008-12-23
> **albinootje said:**
> In a terminal :
```

xboard -size medium

```


oops, i guess i missed this option the first time i checked this huge manpage... lol
thank you so much for finding it :)

---

