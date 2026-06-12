---
title: "Accidently deleted bottom main panel"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by dbuehler on 2009-12-08
I was moving a picture to the trash but dropped it on the panel instead and it did some really weird things.  In the process of trying to correct this problem, I accidently deleted my bottom main panel.   

I was able to create a new one but I can't seem to get it to look and perform the same.  Is there a way to reset it to like it was originally?

---

### Post by macklenc on 2009-12-08
Okay, so you've recreated the main panel and added all of your settings and the menu doesn't work the way it did. Unless you missed a setting along the way the only way I know of resetting the main menu settings is to re-install the OS, I am pretty sure there is a easier and quicker way, but I don't know it.

---

### Post by philinux on 2009-12-08
> **dbuehler said:**
> I was moving a picture to the trash but dropped it on the panel instead and it did some really weird things.  In the process of trying to correct this problem, I accidently deleted my bottom main panel.   

I was able to create a new one but I can't seem to get it to look and perform the same.  Is there a way to reset it to like it was originally?

Open and terminal and use.

```
killall gnome-panel
```

That will restart the panel.
You should be able to add back the bottom panel applets.

However to really get it back to default.
[http://www.celsius1414.com/2006/08/31/how-to-reset-gnome-panel-to-default-in-ubuntugnome2](http://www.celsius1414.com/2006/08/31/how-to-reset-gnome-panel-to-default-in-ubuntugnome2)

---

### Post by dbuehler on 2009-12-08
Thanks Phil.  I tried the link you suggested and all is back to normal now.

---

