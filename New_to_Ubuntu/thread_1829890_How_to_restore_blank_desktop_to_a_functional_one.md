---
title: "How to restore blank desktop to a functional one?"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by babloo75 on 2011-08-20
I have recently installed Ubuntu 11.04 on desktop computer, and found it quite different from previous versions. The panels are not the same as earlier ones and a new "panel" but different type was visible in this new Ubuntu.
The problem started when I tried to create desktop cube with compiz (as in previous versions). Then I fiddled with it and presently the status is that only wallpaper pic is visible when I log in Ubuntu. How to get rid of this? Please help.
And thanks in advance.

---

### Post by beew on 2011-08-20
Right click on the empty desktop to create a new folder. Then open it and navigate to /usr/share/applications where you will find the icon for the Compiz-Configuration-Settings-Manager.  Click to open it and check the Unity box.

I think you can also type > unity --restart in a terminal provided you can start a terminal with ctr+alt+ t

---

### Post by babloo75 on 2011-08-20
Thanks once again. I got it back.

But the desktop switcher does not function anymore.
I feel this useless "unity" is the problem. Can you please suggest a way to remove Unity and revert back to the two panels' option with functional commands (as in earlier versions of ubuntu)

---

### Post by mlg7 on 2011-11-02
I have the same problem under 11.04, but it's not unity, it's gnome. Anyway, this is how I solve it:

At login time, you have to click into the "tambourine" symbol, above the user name. Then, options in the panel below will appear. There, you have to choose "classic without effects". And then, login.

If you choose the wrong option, you may see the forever-in-progress indicator. Don't bother, just reboot.

One more option is to press Ctrl+Alt+F1 ... Ctrl+Alt+F6 and get to one of the 6 text mode consoles; Ctrl+Alt+F7 is the graphical desktop.

There, you can

sudo aptitude install xfce4

but you still will have to hit the tambourine on the login screen with the mouse.
Cannot hit -- your bad.

---

