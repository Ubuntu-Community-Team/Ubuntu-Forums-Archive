---
title: "Compiz &amp; Emerald - Can I have both???"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by jecarr33 on 2009-01-17
I am running Intrepid 8.10.  I currently have Compiz installed with all the SWEET animations and all that other stuff, but I REALLY like the themes that use .emerald file extentions. Can I use an emerald theme but still get all the functions from Compiz??  and Where can I find emerald theme manager for Intrepid??  I always seem to find the theme manager for some other version of Ubuntu.  Please help!!

Jonathan

---

### Post by adult swim on 2009-01-17
yes you can use both.  to get emerald run ```
sudo apt-get install emerald
``` you can find it in System>preferences>emerald when it is installed.  whenever you download emerald themes, once you have imported them to emerald and selected them, you may need to hit alt+f2 and run ```
emerald --replace
``` to get them to work

---

### Post by seagullplayer77 on 2009-01-17
Yup. You can use 'em both. As a matter of fact, I'm using them both right now. Emerald for the window decorator, and Compiz for special effects. If you follow the directions adult swim gave you, you should be OK. The only other thing I can think of is that you *might* have to enable window decorations in Compiz.

---

### Post by jecarr33 on 2009-01-17
> **adult swim said:**
> yes you can use both.  to get emerald run ```
sudo apt-get install emerald
``` you can find it in System>preferences>emerald when it is installed.  whenever you download emerald themes, once you have imported them to emerald and selected them, you may need to hit alt+f2 and run ```
emerald --replace
``` to get them to work

Thank you so much.....turns out you can get it in the Synaptic Package Manager as well...appreciate it very much!!

-Jonathan

---

### Post by mcduck on 2009-01-17
The only way to use Emerald is having both Emerald & Compiz.. ;)

Compiz is a window manager, responsible of turning your programs into windows that can be moved around, resized, minimized and so on. Unlike other window managers (like Gnome's default, Metacity), Compiz doesn't draw window frames, instead it uses a "window decorator" to do that. And that's what Emerald is.

In addition to Emerald, Compiz has two of other window decorators available, the gtk-window-decorator which uses Metacity's themes and kde-window-decorator that uses Kwins themes.

---

