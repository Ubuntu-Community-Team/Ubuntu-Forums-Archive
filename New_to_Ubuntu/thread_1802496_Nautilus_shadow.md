---
title: "Nautilus shadow"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by jermza on 2011-07-12
If I open Nautilus and navigate to, say, Pictures and right-click a file, then the popup menu that appears has no shadow behind it. 

Simply, where in Compiz do I add that shadow?  Under Window Decoration, the relevant field already says "any", so I'm not sure if that's the correct place.

---

### Post by jermza on 2011-07-12
No one?  I know this is a superficial cosmetic query, but I do enjoy a sexy interface.  I've looked around and can't seem to find how to drop a shadow under a Nautilus right-click popup menu.

---

### Post by hhh on 2011-07-12
"any" should have enabled it, but you could also try forcing shadows by entering something like...```
normal | menu | popupmenu | dropdownmenu | dock | tooltip | notification
``` More info here...
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

You're not using RGBA transparency via gtk2-module-rgba, are you? That wreaks havoc with shadows.

---

### Post by jermza on 2011-07-12
I'm not sure.  How do I check that?

It doesn't matter what I do, the shadows aren't appearing.  Does Unity disallow certain styling?

---

### Post by hhh on 2011-07-12
You'd know if you were using gtk2-module-rgba as you would have had to install it.

It's possible Unity is the culprit, but I wouldn't know as I haven't used it. Sorry.

---

