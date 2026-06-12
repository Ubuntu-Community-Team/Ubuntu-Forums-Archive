---
title: "gnome-color-chooser"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by DayLite on 2010-08-08
What is your thoughts on gnome-color-chooser?  I saw [http://gnome-look.org/content/show.php/Sorrow?content=123885 ]("http://gnome-look.org/content/show.php/Sorrow?content=123885")

I am wondering if any on this forum has any thoughts about using it for Ubuntu 10.04?

---

### Post by stinkeye on 2010-08-08
It's not a problem to use on lucid and will not permanently change any of your themes.

It merely writes a line to your **~/.gtkrc-2.0** file which reads...
```
include ".gtkrc-2.0-gnome-color-chooser"
```


Then any changes you make with gcc are stored in **~/.gtkrc-2.0-gnome-color-chooser** and will override your chosen themes gtkrc file.

By clicking the revert button in gcc it clears the **~/.gtkrc-2.0-gnome-color-chooser** file and your theme will be restored.


So if you want to load the **sorrow.gnomecc** (from your link) into 
gcc it won't cause any problems.

---

### Post by DayLite on 2010-08-08
> **stinkeye said:**
> It's not a problem to use on lucid and will not permanently change any of your themes.

So if you want to load the **sorrow.gnomecc** (from your link) into 
gcc it won't cause any problems.

Thank you. How do I 'load' from my link?

---

### Post by stinkeye on 2010-08-08
What I mean is download the **sorrow.gnomecc.tar** file in the link to 
your desktop (anywhere you like really).

Right click on the file > extract here, and you will have a file called
**sorrow.gnomecc**

Open gnome-color-chooser
Click on file > open 
and navigate to where you saved **sorrow.gnomecc** and click apply.
If you don't like it you can adjust the settings in gcc or hit the revert button.

All this is just, someone has used gnome-color-chooser to change the colors of their theme and then saved the config file as **sorrow.gnomecc**
and then posted it to gnome-look.org

The other download (sorrow.emerald) is an emerald theme which changes the appearance of the window titlebar and border.
Emerald themes work only if your using compiz as your window manager.

---

