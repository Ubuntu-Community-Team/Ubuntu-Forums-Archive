---
title: "Removing Metacity"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-03-09
I've put in a "metacity --replace" command into my startup list to get me around a problem I was having with window decoration.

I was wondering why that was necessary. What would be the impact of simply removing metacity?

I've just gone to Synaptic and marked it for Complete Removal, but the list of packages that would also be removed looks a tad worrying, to say the least!

Stuff like gnome-core and ubuntu-desktop would seem to be rather fundamental to my system, I think!

Could someone tell me how deeply embedded metacity is into ubuntu? I thought I used GTK+ and/or compiz to do my screen layout fancy stuff, so why do I still need metacity?

---

### Post by linuxsyst on 2011-03-09
open a terminal and type this:

```
killall compiz && xfwm4 --replace & disown
```

Maybe it will do it.

---

