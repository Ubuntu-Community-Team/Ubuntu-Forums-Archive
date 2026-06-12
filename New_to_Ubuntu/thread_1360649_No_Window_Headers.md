---
title: "No Window Headers"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Swenghk on 2009-12-21
I installed a new font Matrix.ttf, and none of my windows have headers! Even when I switched back to my original Enterprise Bold font! Is it a Compiz problem?

---

### Post by CaptainMark on 2009-12-21
the borders you mean?? 
run:```
metacity --replace
```does that help

---

### Post by Swenghk on 2009-12-21
Nope. Sorry mate! it just got rid of my dock! So I had to do```
compiz --replace
``` to switch it back! I think it is from when I tried to make a transparent terminal... Maybe I messed up somewhere

---

### Post by falconindy on 2009-12-21
For reference, neither Compiz nor Metacity deal with window decorations. In Gnome, that's up to gtk-window-decorator or emerald.

---

