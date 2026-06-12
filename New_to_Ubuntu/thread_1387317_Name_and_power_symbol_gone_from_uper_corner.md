---
title: "Name and power symbol gone from uper corner"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by zappadragon on 2010-01-21
OK so I was doing something and had to reboot. When I logged back in my login name was gone from the upper right hand corner and the power symbol was gone. I want it back and I tried to right click the top bar and then add it back but that is not the same one. Any ideas?

---

### Post by marshmallow1304 on 2010-01-21
Add back "Indicator Applet Session".

---

### Post by zappadragon on 2010-01-21
> **marshmallow1304 said:**
> Add back "Indicator Applet Session".

That just added another envelop for evolution and pidgin notifications

---

### Post by marshmallow1304 on 2010-01-21
That would be "Indicator Applet".  You want "Indicator Applet Session".

---

### Post by zappadragon on 2010-01-21
now when I login I get this error:

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Do you want to delete the applet from your configuration?


Then there is a don't delete or delete button

What have I done?

---

### Post by zappadragon on 2010-01-21
there is no one for "Indicator Applet Session".

---

### Post by zappadragon on 2010-01-21
Now under System I have lock screen, log out , and shutdown but I really want it back to the old way where it was in the simple login name and power button icon. Please help

---

### Post by cenzorrll on 2010-01-22
looks like it got uninstalled

```
sudo apt-get install indicator-applet-session
```

make sure you don't say yes until you read what files are being installed (not usually too important) and what is being removed (extremely important, especially considering how I think you lost it in the first place)

if you don't want the packages installed or it removes a package you need, then you shouldn't proceed.

if it just goes ahead without asking you're fine

---

### Post by tom.swartz07 on 2010-01-22
> **cenzorrll said:**
> looks like it got uninstalled

```
sudo apt-get install indicator-applet-session
```

make sure you don't say yes until you read what files are being installed (not usually too important) and what is being removed (extremely important, especially considering how I think you lost it in the first place)

if you don't want the packages installed or it removes a package you need, then you shouldn't proceed.

if it just goes ahead without asking you're fine
That should take care of it.
If that doesnt fix it, you could just reset your panel settings.



In a terminal, type ```
sudo cp ~/.gconf/apps/panel ~/.gconf/apps/panel_old && sudo rm -rf ~/.gconf/apps/panel
```

That will move your old settings for your panel to a backup file remove any changes you made to your panel. When you log out and log back in, it should fix itself.

Hope this helps!

---

### Post by zappadragon on 2010-01-22
Thanks but that did not work either. I guess I might just have to reinstall ubunutu all together.

---

