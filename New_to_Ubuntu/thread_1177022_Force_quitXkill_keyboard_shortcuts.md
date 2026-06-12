---
title: "Force quit/Xkill keyboard shortcuts?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-02
1.Is there a keyboard shortcut for force quit?
2.Is there any way to put the force quit applet/shortcut into my menus rather than panel?
3.In the Xkill command, is there any way to cancel the skull and the operation? (like pressing esc in force quit cancels the force quit operation).
4.What does ctrl+alt+backspace do? Shouldn't it kill X? For me it does nothing, as if there is no binding? So how do I kill X?

---

### Post by pspsampsp on 2009-06-03
check here [https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace)

i think you just have to install dontztap (sudo apt-get install dontzap) 
and then run the command 'sudo dontzap --disable'

---

### Post by mcduck on 2009-06-03
> **Andy06 said:**
> 1.Is there a keyboard shortcut for force quit?
2.Is there any way to put the force quit applet/shortcut into my menus rather than panel?
3.In the Xkill command, is there any way to cancel the skull and the operation? (like pressing esc in force quit cancels the force quit operation).
4.What does ctrl+alt+backspace do? Shouldn't it kill X? For me it does nothing, as if there is no binding? So how do I kill X?

1. I don't think there is.
2. No. It's not a shortcut, it's a panel applet (as in "a program that runs in the panel")
3. Sure. Press any other mouse button than the left button.
4. It *used to* kill X, now it's disabled by default. You ca enable it again in xorg.conf, but Alt-SysRq-k will give the same result and still works out-of-the-box.

---

### Post by Andy06 on 2009-06-03
Thanks Mcduck, solves everything.

---

