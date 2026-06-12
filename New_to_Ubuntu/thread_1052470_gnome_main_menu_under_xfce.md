---
title: "gnome main menu under xfce"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by matthew.ball on 2009-01-27
I recently installed xfce, being a fan of fluxbox, this is awesome.

My only gripe is it uses the gnome main menu, but doesn't take into account the items you have "greyed" out (i.e. Not visible in the gnome session).

So, while I have customised my gnome main menu to look exactly how I want, the same can't quite be said for xfce.

I figured it would be faster if I could just export the current gnome menu, and edit that, then re-load into xfce and everything would be good.

Is that possible?

Also, looking for custom icons for xfce, where are gnome applications icons located?

Thanks for any help.

---

### Post by m_duck on 2009-01-28
XFCE uses its own menu by default.  You can edit it by right clicking the menu button on the panel and clicking edit menu, or, for more control, edit the config file at ~/.config/xfce4/desktop/menu.xml and just adding/removing the applications as menus as you wish. There is another version of the menu with a lot of comments at /etc/xdg/xfce4/desktop/menu.xml to give you a better idea of how to do it.

Any icons that you have installed in Gnome are probably in the ~/.icons folder in your home directory. To add more icons, you can get them from [gnome-look](http://www.gnome-look.org) or wherever and extract the icon folder into ~/.icons. You can then choose XFCE to use the icons by going to Settings -> Settings manager (in the main menu) and click "User interface". In this window, click the icon theme tab and all of your install icon themes should show up (the original icons are installed at /usr/share/icons).

Hope this is of some use.

---

