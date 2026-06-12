---
title: "Can anyone help me with my screensavers?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by djneve on 2009-03-08
One little thing I really enjoy is putting my screen saver on when I leave the laptop and having it function as a slide show for the children.  For this I always us "Pictures folder" but I find that it picks up pictures from ALL my directories.

Question; is there any way to specify exactly WHICH directory I'd like it to use?  I'd assumed it would default to ~/Picutes but no, anything in my home directory is fair game -- not good!

In the same vein, is there any way to specify which folder the "GLSlideshow" should use?

Thank you so much!

Derrick

---

### Post by ajgreeny on 2009-03-08
Try this:-
Screensaver pictures folder change
/usr/share/applications/screensavers/personal-slideshow.desktop

Edit the Pictures folder configuration file:

```
gksudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop
```Find the line (near the bottom in mine, line 138)
```
Exec=slideshow --location=Pictures
```In Hardy Heron and later the line is simply ```
exec=slideshow
``` To customize the location, just add ```
--location=PATH
``` where PATH is the location of your pictures and change it to
```
Exec=slideshow --location=/path/to/your/Pictures_folder
```Good luck.

---

