---
title: "No mouse, need to get network manager"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by adult swim on 2009-02-08
I have borked my touchpad and I can't get on the Internet to fix it.  Does anyone know how to get the network manager up with the keyboard?  I've tried launchinng nm-applet but it starts on the tray where I can't get to it.

---

### Post by 3rdalbum on 2009-02-08
Press Alt-F2 and type:

```
gnome-at-properties
```

Press Enter.

Now press Tab until you get to "Enable assistive technologies" and press the space bar. Keep tabbing until you get to "Keyboard Accessibility" and press Space. Press right arrow until you get to the Mouse Keys tab. Tab down to "Use keypad as mouse" and press space bar.

Press Alt-F4 to close the window, and then tab down to "Close and Log Out". Press spacebar. When you log in, you should be able to use numeric keypad as a mouse, which will enable you to use Network Manager.

On a laptop your "numeric keypad" is probably when you hold down the "Fn" key and press the WASD keys or something similar - check what's printed on your keys to find out exactly what acts as the numeric keypad.

---

### Post by MyR on 2009-02-08
@3rdalbum
I just want to say: That's awesome!

---

### Post by jualin on 2009-02-08
> **3rdalbum said:**
> Press Alt-F2 and type:

```
gnome-at-properties
```

Press Enter.

Now press Tab until you get to "Enable assistive technologies" and press the space bar. Keep tabbing until you get to "Keyboard Accessibility" and press Space. Press right arrow until you get to the Mouse Keys tab. Tab down to "Use keypad as mouse" and press space bar.

Press Alt-F4 to close the window, and then tab down to "Close and Log Out". Press spacebar. When you log in, you should be able to use numeric keypad as a mouse, which will enable you to use Network Manager.

On a laptop your "numeric keypad" is probably when you hold down the "Fn" key and press the WASD keys or something similar - check what's printed on your keys to find out exactly what acts as the numeric keypad.

You can also access the Main menu by pressing ALT+f1.

---

### Post by adult swim on 2009-02-08
3rdalbum that was awesome advice!  Thanks man I appreciate it!

---

