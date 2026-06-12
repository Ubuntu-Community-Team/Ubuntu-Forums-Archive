---
title: "How to limit Compiz-Fusion to 3 of 4 viewports?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by 11010110 on 2009-08-06
Hey all,

I was wondering if there was any way possible to limit compiz fusion to act on only 3 out of the 4 workspaces I have set up. The reason I'd ask such an odd thing is that i compiled a program called ProjectM (it is just like milkdrop for those who are familiar with what that is). The problem is for some reason it doesn't like to play nice with CF and causes some glitching and stuttering. If I could keep one workspace CF free while keeping it going on all others it would be perfect for me. 

Thanks to all in advance!

---

### Post by barnex on 2009-08-06
I'm pretty sure that's not possible, but you could install fusion-icon (it's in the repo's). This lets you quickly switch compiz on and of. There's also an analogous plasmoid for kde.

---

### Post by 11010110 on 2009-08-06
I have compiz icon as well as compiz switch installed so i can turn it on and off with a simple keystroke which is ok but the problem lies in the fact that when i do switch off CF every program from every viewport becomes consolidated in desk 1 and then when I do decide to turn CF back on i have to arrange them all back in place and that is a hassle especially for some programs that do not take easily to being dragged across viewports. any ideas on how to force open windows to maintain their positions upon the disabling of CF?

Thanks again!

---

### Post by londonali1010 on 2009-08-06
I'm not sure if this helps, but I know you can define what windows to apply, for instance, window decorations to, by including or excluding window types, classes, names, etc.  It's probably worth poking around the general Compiz settings to see if you can turn off the effects just for that window type.

As an example, you can turn off window shadows for just one class of window by putting in "any& !(class=Conky)" -- this applies shadows to all windows whose class is defined as something other than Conky.

I would have a go myself but I'm currently on a Windoze 'puter :-\" and my Ubuntu system is at home!

---

### Post by Humanum on 2009-08-06
Hi,


Whitout compiz fusion working, do you normally have your 4 desktop ?

---

### Post by 11010110 on 2009-08-06
Thanks for the tip londonali1010. sadly though for some reason that is not working for me... I will keep messing with it to see if it will work eventually lol. and also yes I have 4 viewports with and without CF.

---

### Post by 3rdalbum on 2009-08-06
The window manager handles viewports (virtual desktops) as well as the locations of your windows. So no, there's no way to do what you suggest.

KDE's Kwin window manager can run in non-composited mode, if you don't mind a switch to KDE. Then you can disable compositing and not have all your windows appear on Desk 1.

---

### Post by 11010110 on 2009-08-06
It would be far too much of a hassle to switch over to KDE. So there is no way for gnome to support what you say KDE does?

---

