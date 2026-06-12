---
title: "Top Bar won't allow full screen in Wine"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Knightsfoil on 2011-07-15
I can't play Starcraft 2 in full screen. The top bar appears with "Wine Windows Program Loader". I am launching from Terminal, but the same thing happens if I launch wine from terminal first and then launch Starcraft. If I switch terminal to fullscreen and then launch, the game opens behind the terminal window.

Full screen works in both Movie Player and Firefox.

I have Natty 64 bit clean install (dual boot Win7) and Wine 1.2.3 installed from tar. I have the launchbar set to AutoHide.

If I exit game and relaunch several times I can occasionally get Starcraft 2 to launch in fullscreen.

Is there a fix for this or a way to hide the top bar? Should I ditch Unity for gnome classic?

---

### Post by beew on 2011-07-15
Try this.

Open  Configure Wine > Graphics and uncheck "Allow window manager to control the windows"

---

### Post by Knightsfoil on 2011-07-16
Thanks beew! You resolved my issue!!! :o

---

