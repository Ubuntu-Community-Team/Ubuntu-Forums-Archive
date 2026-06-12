---
title: "Set window to urgent? (Compiz)"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by linkmaster03 on 2009-02-03
I'm on 8.10 with Compiz, and I'm wondering how I can set a window to urgent. I'm looking for some kind of signal that I can send to a chosen window from a shell.

By urgent I mean the flashing behavior that Pidgin uses to notify you that someone has IMed you.

---

### Post by linkmaster03 on 2009-02-06
I found out how to do it. This is how I did it.

Install wmctrl.

```
sudo aptitude install wmctrl
```

Now, type this:

```
wmctrl -r <part of window title> -b add,demands_attention
```

What you pass to -r is searched in your window titles and the appropriate window is selected. To use an exact window title (case-sensitive too), add -F in the option list.

**(thanks to "maniac" from Compiz forums)**

---

