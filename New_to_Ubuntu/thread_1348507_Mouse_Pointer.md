---
title: "Mouse Pointer"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by expatCM on 2009-12-07
I need to change the color of the mouse pointer to make it easier to see.

Is there a straight forward way of doing that?

---

### Post by howefield on 2009-12-07
Try going into System > Preferences > Appearance, then press the Customise button on the Theme tab, then go into the Pointer tab and set as required.

Not a lot of choice, but does it meet your needs ?

---

### Post by JamesParnell on 2009-12-07
go here: 
[http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=0c18ac484cdba79cc07e16f5c84f0c6d](http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=0c18ac484cdba79cc07e16f5c84f0c6d)
 
they have a wide range of mice, mouses, whatever...to download. simply downlad the tar.gz file to your desktop (its easier), right click the desktop, click "change desktop background", click the "theme" tab, and drag the tar.gz file you downloaded into the theme box...it will them tell you either "the theme has been installed" or " would you like to keep the current or apply the new theme", click **apply, **log out and back in***** and you have a new cursor
 
***i have had a few bugs with cursors not updating fully without a log in/out.**
 
**also, to change the mouse to an other downloaded ones, do as howefield said and click the customise button in theme tab.**

---

### Post by JamesParnell on 2009-12-07
let me know if that work, would be nice to get something right for a change :P

---

### Post by LuisGMarine on 2009-12-07
> **JamesParnell said:**
> go here: 
[http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=0c18ac484cdba79cc07e16f5c84f0c6d](http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=0c18ac484cdba79cc07e16f5c84f0c6d)
 
they have a wide range of mice, mouses, whatever...to download. simply downlad the tar.gz file to your desktop (its easier), right click the desktop, click "change desktop background", click the "theme" tab, and drag the tar.gz file you downloaded into the theme box...it will them tell you either "the theme has been installed" or " would you like to keep the current or apply the new theme", click **apply, **log out and back in***** and you have a new cursor
 
***i have had a few bugs with cursors not updating fully without a log in/out.**
 
**also, to change the mouse to an other downloaded ones, do as howefield said and click the customise button in theme tab.**


you can just fire up terminal and type in to refresh gnome after theme changes:

```
killall gnome-panel
```

---

### Post by JamesParnell on 2009-12-07
noted..thanks for that tip

---

### Post by expatCM on 2009-12-08
system / preferences / appearance / customize and then select a pointer and make the pointer larger is easy and does fix my need.  Thank you all for the help :)

---

