---
title: "Top bar of windows not appearing"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by psam3 on 2009-12-19
So I just turned my computer on, and there is no top bar on any of the windows, the one with the close, minimize, and maximize buttons. Maybe it is there, but the buttons aren't showing up. Last time I was on, I was fooling around with system themes and Emerald and Compiz and all that. I don't know what I did, but is there any way to bring those buttons back? I tried setting everything back to default, but nothing. 

Thanks

---

### Post by slughappy1 on 2009-12-19
Go to CompizConfig Settings Manager and take a screenshot of Effects->Window Decorations.

---

### Post by 3rdalbum on 2009-12-19
Try hitting Alt-F2 and typing:

```
metacity --replace
```

Because it looks like your window manager is not starting.

---

### Post by psam3 on 2009-12-19
> **slughappy1 said:**
> Go to CompizConfig Settings Manager and take a screenshot of Effects->Window Decorations.

> **3rdalbum said:**
> Try hitting Alt-F2 and typing:

```
metacity --replace
```

Because it looks like your window manager is not starting.

I figured it out, thanks. The window decorator was set to Emerald instead of GTK

---

### Post by joes7 on 2009-12-19
Open a terminal and write:xfce4-panel

---

### Post by MelDJ on 2009-12-20
reload/change the window manager

---

