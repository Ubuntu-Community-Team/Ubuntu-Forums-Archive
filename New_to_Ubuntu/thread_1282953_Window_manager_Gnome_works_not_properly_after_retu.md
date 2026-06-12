---
title: "Window manager Gnome works not properly after returning from Awesome"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by realalien on 2009-10-05
When I tried to use Awesome window manager, I just found that basic installation changed my total user experience, but when I changed back, the title bar is missing. All hotkeys are gone. Quite uncomfortable feelings.

My question is how to reset/configure the Gnome window manager?

Thanks in advance.

---

### Post by tom.swartz07 on 2009-10-05
First, Back up any data that you dont want accidentally lost.
Through the terminal, run the command

```
sudo apt-get install --reinstall ubuntu-desktop
```
That should reinstall Gnome, and get you back to the 'out-of-the-box' setup that you have from a fresh install. From there you might have to re-enter any custom hotkeys that you setup, but the default ones should be working.

Hope this helps!
Tom

---

### Post by realalien on 2009-10-05
Thanks for the reply! The solution looks simple but great! Now I am trying to configure using pre-installed GUI tools.

---

