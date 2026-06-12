---
title: "Metacity Theme Refresh"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-04-27
hi!
I'm editing a theme, and want to refresh metacity, because a simple theme switch does not refresh the metacity images, like minimize, max, and close.

I've had a reasonable look around and find that commands starting with metacity-message, don't seem to work anymore!

Any help would be !! OH, So NICE! :D
TFC!
Robin

---

### Post by mcduck on 2009-04-27
"metacity --replace"

(or in worst case: "killall metacity && metacity --replace")

If that doesn't work, make sure you are actually using Metacity and not Compiz with Gnome-Window-Decorator (which would be the default setup when you have desktop effects enabled)...

---

### Post by hungryOrb on 2009-04-27
> **mcduck said:**
> "metacity --replace"

(or in worst case: "killall metacity && metacity --replace")

If that doesn't work, make sure you are actually using Metacity and not Compiz with Gnome-Window-Decorator (which would be the default setup when you have desktop effects enabled)...

Thanks for reply! :)
You couldn't point me in a more specific direction as to how to refresh compiz using the GWD or similar could you? thanks for considering :D

Robin

---

### Post by jespdj on 2009-04-27
For reloading Compiz,
```
compiz --replace
```
should also work. (I didn't try it out).

---

