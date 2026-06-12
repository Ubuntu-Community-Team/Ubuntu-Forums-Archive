---
title: "How might I set different wallpapers for different workspaces?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by diablo75 on 2009-04-30
I seem to remember there being a "hack" method that you could use with Compiz to put multiple desktops wallpapers on different workspaces, and that this was eventually going to be developed into a supported feature that didn't require any hacking to get working.  Anyone know if this has actually been implemented yet?

---

### Post by spiderbatdad on 2009-04-30
unfortunately not supported to my knowledge. workspaces exist on a single desktop

>  Every workspace contains the same desktop, the same panels, and the same menus. However, you can run different applications, and open different windows in each workspace.
[http://library.gnome.org/users/user-guide/stable/overview-workspaces.html.en](http://library.gnome.org/users/user-guide/stable/overview-workspaces.html.en)

---

### Post by Tibuda on 2009-04-30
You can set different wallpapers if you enable and setup the wallpapers plugin in compiz settings manager (System > Preferences > Desktop effects), but it will only work if you disable Nautilus desktop in gconf-editor under /app/nautilus/preferences/show_desktop, and you won't be able to have icons in your desktop (unless you use the [folderview screenlet]("http://www.gnome-look.org/content/show.php/Folderview+Screenlet?content=102890")).

---

### Post by spiderbatdad on 2009-04-30
[http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10](http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10)

I seem to recall the operation has to be supported by your graphics card as well.
You will also loose your icons.

---

### Post by MontelEdwards on 2009-04-30
> **spiderbatdad said:**
> [http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10](http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10)

I seem to recall the operation has to be supported by your graphics card as well.
You will also loose your icons.
I hang around Ubuntu Brainstorm a lot, and this idea is still in voting process.
Expect to see it soon, because right now it is at 500+.

---

### Post by Lonewolf321 on 2009-05-07
You could give another program a try.  It is called Wallpapoz, it can be found at [http://wallpapoz.akbarhome.com](http://wallpapoz.akbarhome.com) . I use it on my system even running compiz.  Doesn't work as fast as the KDE changer but at least it works. Can be run as a service or you can start it manually.  Has a few different options that can rotate wallpapers at certain time intervals. Hope this helps and works for you.

---

