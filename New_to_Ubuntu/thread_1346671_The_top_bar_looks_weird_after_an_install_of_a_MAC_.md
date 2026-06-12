---
title: "The top bar looks weird after an install of a MAC theme"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by retskrad on 2009-12-05
I just installed Mac4Lin (mac theme) and then I removed it. But I can't restore the look of ubuntu. I have tried to restart. but nothing. Here's a pic of the top bar:
I want to restore it to the default, I want the selected are to be on the RIGHT side.
[IMG]http://i47.tinypic.com/kamluu.png[/IMG]

---

### Post by retskrad on 2009-12-05
also, I have ubuntu 9.04.

---

### Post by coffeecat on 2009-12-05
> **retskrad said:**
> also, I have ubuntu 9.04.

Are you sure? The upper panel on your screenshot looks like 9.10.

Anyway...

Press Alt-F2 and type in *gconf-editor* to launch the Gnome configuration editor. Go to apps -> metacity -> general. Double-click on "button_layout" in the right pane. Change the text there to:

```
menu:minimize,maximise,close
```

---

### Post by retskrad on 2009-12-05
I did that, but still the top bar hasnt changed.

---

### Post by BinaryFeast on 2009-12-05
> **retskrad said:**
> I did that, but still the top bar hasnt changed.

Did you restart your session / reboot afterwards?

---

### Post by retskrad on 2009-12-05
Yes, i retstarted. and now the top panel is totaly gone, and the the top par of the window, still the same.

---

### Post by coffeecat on 2009-12-05
> **retskrad said:**
> Yes, i retstarted. and now the top panel is totaly gone, and the the top par of the window, still the same.

Go back into gconf-editor and check the code again. My apologies - I made a typo. Being British I typed maximise instead of maximize, although I doubt whether that would have made the panel disappear. Anyway, the code should be:

```
menu:minimize,maximize,close
```That's - menu COLON minimize COMMA maximize COMMA close -

Then try restarting the session and see if the panel is still missing. If you need to, you can put the panel back by right-clicking on the lower panel > New Panel and mouse-moving to the top. Then you'll have to put all the applets back.

---

