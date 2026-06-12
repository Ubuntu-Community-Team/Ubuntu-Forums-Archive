---
title: "Wierd windows 7 look problem"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by Elfyy on 2011-07-21
So, I tried this tutorial: [http://www.howtogeek.com/55985/how-to-make-ubuntu-linux-look-like-windows-7/]("http://www.howtogeek.com/55985/how-to-make-ubuntu-linux-look-like-windows-7/") But after a little I realized how much I hate the look of windows 7!  SO I uninstalled it the way it says w/ the uninstall file which worked except the bar at the top of the windows... It still looks like win 7. I tried the other way it says and still didn't work, I also switched themes and it still wont fix it. Any ideas? Thanks!

---

### Post by Terl on 2011-07-21
Did you try everything on that page including this:

```
Forcefully uninstalling

In some cases when you try uninstalling the theme it won’t uninstall completely, leaving some Windows 7 icons or desktop wallpaper. In cases like this, you’ll have to remove the theme by deleting it’s files manually but don’t worry, it is easier than you think. Just open up a terminal window and type the following command followed by the enter key.

    rm -rf .gnome .gnome2 .gconf .gconfd .metacity

NOTE: This will restore your gnome appearance setting back to the default like when you first installed Ubuntu.
```

That should fix it all.

---

### Post by MG&amp;TL on 2011-07-21
I would be VERY careful with the 'forcefully uninstalling' command, it looks horribly like the ones found here:

[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

If you trust the site, fine, but just be very careful with your typing. :)

---

### Post by Elfyy on 2011-07-21
I tried that and it did nothing...

---

### Post by Elfyy on 2011-07-21
Any Ideas???

---

### Post by lkjoel on 2011-07-21
Type in a Terminal window:
```
rm -rf ~/.emerald
```
This will reset the titlebar theme.

---

### Post by beew on 2011-07-21
> **lkjoel said:**
> Type in a Terminal window:
```
rm -rf ~/.emerald
```This will reset the titlebar theme.

You just need to change the emerald theme or go to ccsm and choose the default window decorator instead of emerald (can't remember what it is as I do use emerald though not the dreadful win7 theme)

---

