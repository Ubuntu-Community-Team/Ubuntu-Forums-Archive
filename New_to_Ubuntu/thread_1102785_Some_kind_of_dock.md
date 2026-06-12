---
title: "Some kind of dock"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by theozzlives on 2009-03-22
I can't figure out cairo or AWN. I want a docking program can someone help?

---

### Post by Perfect Storm on 2009-03-22
What do you mean?

---

### Post by James_Lochhead on 2009-03-22
> **theozzlives said:**
> I can't figure out cairo or AWN. I want a docking program can someone help?

Copy this:

```
sudo apt-get -y install cairo-dock avant-window-navigator
```

Go to Applications > Accessories > Terminal

Click the terminal window, hold ctrl and shift, press v, let go on shift and ctrl then press enter.

Close the terminal window.

Press alt + f2.

In the window that pops up press cairo-dock or avant-window-navigator (exactly) then press enter. The one you picked will now load at the bottom of the screen. Cairo is hidden by default so just move your mouse down and it will pop up.

If you want one enabled when you log in go to System > Preferences > Sessions. Press the add button. In the name field type Dock. In the command field type cairo-dock or avant-window-navigator then press ok.

It really does not get much simpler to cairo/awn.

I suggest cairo btw. I find awn very buggy.

---

