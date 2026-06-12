---
title: "Alt-F2 issues"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by UpSignal on 2011-02-12
Guys, my alt-F2 stoped working. I red a high number of threads and numerous cases of ppl with this issue, and i'm feeling like an idiot, i simply can't fix this.

The last thing i recall doing, was.... installing and activating compiz effects, and also installed AWN. I completely removed gnome panels, i'm just using awn. Can any of this things break alt f2? 
i red some ppl saying: oh activate gnome compatibilty in compiz. Well, that's already activated by default. I'm out of ideas! it was working 2 days ago!

btw, i deleted my gnome panel with this command:
sudo mv /usr/bin/gnome-panel ~/.panel

---

### Post by Ctrl-Alt-F1 on 2011-02-12
Sounds like it's because of what you did with gnome panel.  Anyway, you didn't delete gnome panel.  You just moved it.
try:

sudo mv ~/.panel /usr/bin/gnome-panel
logout, log back in

You can't delete ALL the panels but you can hide the last one so that it doesn't show up at all.

---

### Post by mcduck on 2011-02-12
> **UpSignal said:**
> Guys, my alt-F2 stoped working. I red a high number of threads and numerous cases of ppl with this issue, and i'm feeling like an idiot, i simply can't fix this.

The last thing i recall doing, was.... installing and activating compiz effects, and also installed AWN. I completely removed gnome panels, i'm just using awn. Can any of this things break alt f2? 
i red some ppl saying: oh activate gnome compatibilty in compiz. Well, that's already activated by default. I'm out of ideas! it was working 2 days ago!

btw, i deleted my gnome panel with this command:
sudo mv /usr/bin/gnome-panel ~/.panel
Well, there's your problem. The Run dialog that you get with the Alt-F2 shortcut is a feature of the Gnome-panel. No panel, no run dialog with Alt-F2.

Anyway, if you don't want to use Gnome-panel, there are several other applications that provide such dialog, just pick one you like and then bind the Alt-F2 shortcut to launch it.

You could try Alawalk, GRun or Gmrun, for example.

(Also there's no reason to mess with the gnome-panel binary just to get the panel away from your desktop. It can be removed or replaced by other panel/dock app through gconf.)

---

### Post by UpSignal on 2011-02-12
thanks for the tips guys, i'm gonna try to hide it with gconf :)

---

