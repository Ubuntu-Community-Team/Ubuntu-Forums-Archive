---
title: "Fonts icon disappeared"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-07-24
The fonts icon in Ubuntu software center has turned blank. Oddly enough, it's happened on both my machines running 10.04, so I don't think it was my doing. Was there something in a recent update that might have caused this?

---

### Post by wojox on 2010-07-25
I just checked and I don't have the font icon either. Must be a bug.

---

### Post by Frogs Hair on 2010-07-25
If you have changed your Icons it may not be included in the set . I have tried many icons sets and the font icon is missing in many.

---

### Post by Chris1274 on 2010-07-25
Good call, I did change to the gnome icons on both machines.

---

### Post by tomofpittsburgh on 2010-08-22
I have it too, but if I don't see those icons changing with desktop icons.  What icons are we talking about here?

---

### Post by Vrroom on 2010-08-22
if you download some user created icon sets, they may may not include icons for each and every category in software center. Its not a bug. Just that the icon set you have currently applied have some missing icons.

---

### Post by Andrew_P on 2012-02-10
The disappearing icons are an artifact of using a desktop theme that doesn't include the necessary icons for Ubuntu Software Center.  This can be demonstrated by starting the system with the LiveCD.  Ubuntu 10.04 uses Humanity in its new default theme.  If you run Ubuntu Software Center, you'll see that all the top level and sub-menu icons are populated.  Then, switch to the Clearlooks theme and restart Software Center.  You'll see that the Fonts icon is missing, as well as many icons in various sub-menus.

You can either live with the quirk, or put links to the missing icons in /usr/share/icons/gnome/scalable/categories.  Open Nautilus File Manager as root (command: sudo nautilus), navigate to /usr/share/icons/Humanity/categories/48, then open a second tab and navigate to /usr/share/icons/gnome/scalable/categories.  Create symbolic links from the icons you'll need in /usr/share/icons/Humanity/categories/48, then cut/paste them into /usr/share/icons/gnome/scalable/categories.  Rename the links to remove the "Link to " part in the beginning.  After you've made all the links you need to populate the Software Center, execute the following command in a terminal window as root to force a rebuild of the icon cache:

sudo gtk-update-icon-cache --force /usr/share/icons/gnome

It may take a minute or two for all the icons in open windows to be updated.  If you've done everything right, the next time you restart Ubuntu Software Center all the icon spaces in the category menus should be populated.

(I happen to like Clearlooks, and I wrote this description based on what I've encountered with that theme.  It's possible that other themes exhibit this problem.  You may have to adjust the file paths as necessary.)

---

