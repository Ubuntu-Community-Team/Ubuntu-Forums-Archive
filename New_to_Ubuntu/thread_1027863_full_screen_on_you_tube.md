---
title: "full screen on you tube"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Vic! on 2009-01-01
Full screen mode on lots of flash players seems to not be working is there a way to fix this thank you any help is much appreciated

---

### Post by nemilar on 2009-01-01
What do you mean, specifically, when you say "not working?"  what is the behaviour you experience?

---

### Post by stderr on 2009-01-01
I normally find Compiz to be the problem, although not always. So, a couple things I'd recommend:

You can make use of a Compiz feature as a kinda hacky workaround. If you haven't already got the Compiz Config Settings Manager, run this in a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

and let it install. Then goto System -> Preferences -> CompizConfig Settings Manager.

You can enable 'Enhanced Desktop Zoom' by clicking on the box beside it. You should then be able to zoom into your desktop with WINDOWSKEY (otherwise called META or SUPER) and moving the mouse wheel up at the same time. Zooming out is achieved by moving the mouse wheel down. You can 'lock' the view at any given time with META and L. You use META and L again to unlock it. 

The other thing I'd suggest is trying the Metacity window manager in place of Compiz, to see if that works properly. To easily switch between window managers, you need to install fusion-icon.

```
sudo apt-get install fusion-icon
```

and let it install.  Then, you can goto Applications -> System Tools -> Compiz Fusion Icon.

A blue icon will appear in your system tray. If you right click on it, and choose Select Window Manager -> Metacity, your WM will change instantly (takes a few seconds to complete). Then give fullscreen video a go again; any difference?

edit: Oh, and you can revert to Compiz by repeating the above step, but selecting Compiz instead of Metacity.

---

### Post by Vic! on 2009-01-01
Thank you for the help i will try this. STDER. nemilar, when i click full screen it goes to full screen for a split second then it reverts back to the normal mode as if it automatically clicked esc. also

---

### Post by jerrrys on 2009-01-01
or just use "Miro"

---

