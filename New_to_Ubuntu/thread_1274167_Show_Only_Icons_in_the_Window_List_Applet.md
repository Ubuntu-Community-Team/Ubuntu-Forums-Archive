---
title: "Show Only Icons in the Window List Applet"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by coldReactive on 2009-09-24
I want to show only icons in the window list applet, rather than the entire name of the window, is this possible in GNOME/Ubuntu or even Kubuntu and Xubuntu?

---

### Post by Marflus on 2009-09-24
window-picker-applet displays only icons for any windows which aren't maximised. It may suit you, but it's as near to only icons as I can find.

```

sudo aptitude install window-picker-applet

```

Or install from Synaptic Package Manager. You can add it to the panel just like window list once installed.

---

### Post by coldReactive on 2009-09-24
> **Marflus said:**
> window-picker-applet displays only icons for any windows which aren't maximised. It may suit you, but it's as near to only icons as I can find.

```

sudo aptitude install window-picker-applet

```

Or install from Synaptic Package Manager. You can add it to the panel just like window list once installed.

Yeah, that's the problem, I need it for maximized as well. Plus, the wind-picker applet shows the currently focused app in all workspaces, not a good idea.

---

### Post by Marflus on 2009-09-24
Hrm, then unless you fancy editing the source code of window-picker I'm not much use, I'm afraid. I don't know of any applets that do what you want.

---

### Post by nortexoid on 2009-11-21
Try dockbar or dockbarx. The latter is the experimental version of dockbar. It's got a few more features and it's rock solid stable on my system.

The only thing that annoys me about the applet is that you can't (well, I can't see how to anyway) set it to show only windows on the current workspace. This might not bother you.

---

