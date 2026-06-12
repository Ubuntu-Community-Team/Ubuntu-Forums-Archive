---
title: "Switch workspace shortcut"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by gzav on 2009-07-04
Hi all,

I know of the usual shortcut for switching workspace (ctrl - alt - left/right) but i was wondering if it's possible to change that shortcut to something easier. For example, I'd like to assign the windows key to switch workspace. I know how to assign a shortcut key to an application (settings - keyboard - application shortcuts) but I'm not sure how to proceed to select "switch workspace". Is there a command line that switches workspace that I could assign to the win key?

Thanks in advance

---

### Post by CatKiller on 2009-07-04
> **gzav said:**
> I know of the usual shortcut for switching workspace (ctrl - alt - left/right) but i was wondering if it's possible to change that shortcut

Install compizconfig-settings-manager, then 
System -> Preferences -> CompizConfig Settings Manager -> Rotate Cube (or Desktop Wall if you're using that instead)

The keybindings are listed there.

You probably don't want to use the Windows key on its own though. It's a modifier for a whole bunch of other shortcuts. Especially if you are using Compiz.

EDIT: Just noticed you're using Xfce. I don't know much about the settings there. But you might still be using Compiz for your Window Manager, in which case the above will still all work.

---

### Post by gzav on 2009-07-09
Nope, I'm not using compiz, it's a bit too heavy for my rig, I'm just using the regular xfce4 window manager

---

### Post by sisco311 on 2009-07-09
Menu -> Settings -> Window Manager - Keyboard tab

---

### Post by boblemur on 2009-07-09
its under normal key bindings, if compiz is disabled:

system > preferences > keyboard shortcuts (not sure about xfce though)

also if you want to use windows keys as part of shortcuts, you need to goto:

system > preferneces > keyboard (not sure about xfce though)

click the layout tab, then click layout options, select alt/win key behaviour and set "Super is mapped to Win Keys"

then click ok, it will the come up as mod4 when you use it in setting shortcuts.

i dont know why u have 2 do the second part but iv always had to...

---

