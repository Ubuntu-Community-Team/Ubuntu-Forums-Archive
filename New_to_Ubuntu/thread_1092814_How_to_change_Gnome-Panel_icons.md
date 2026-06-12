---
title: "How to change Gnome-Panel icons?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by NK-Magi on 2009-03-10
I'm currently running Gnome-Colors with Shiki-Wise on my laptop, but I'm wanting to change the volume tray icon and the wireless tray icon to the default Human ones.  I've tried copy and overwriting them in /usr/share/icons but for some reason it won't change.  I've also looked in gconf-editor but I can't find any place to put the right entry to replace the icon.

Any ideas?

---

### Post by BDNiner on 2009-03-10
The icon files you need to change would be the ones in .icons folder in your home folder.

---

### Post by Temposs on 2009-03-10
Go to System->Preferences->Appearance, click Customize, click the Icons tab, and look to see which icon theme you have selected. You may have this theme located either in /usr/share/icons or ~/.icons

You need to replace the icons you want to replace for every single size icon in the theme. You'll notice in the theme's directory there are directories like 8x8, 16x16, et cetera, which represent the size of the icons in that directory.

---

### Post by NK-Magi on 2009-03-10
Mmk that worked, had to purge both /usr/share/icons and .icons (I didn't know about that one) and replace them and it works fine now!

Thanks!

---

