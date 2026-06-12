---
title: "ubuntu 10.04 visual help"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by tamim_lio on 2010-04-29
hi,
   right now i am using ubuntu 10.04 LTS . i like the visual effect a lot . i have compiz fusion installed and currently using emerald window decorator. i want the top taskbar fully transparent . i right clicked on the panel and used the background solid color . but the " Application place system " are and the right most area are not transparent.just the middle part of the panel is transparent. i want the whole panel transparent. how sould i do that ? please help .

---

### Post by AndyBoy_LV on 2010-04-29
It`s impossible, gnome-panel does not support that. You cannot make icon tray transparent. However, if you feel like experimenting, you can try another panel - tint2 ([http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)) - it does allow that.

---

### Post by ijustwantyourhalf on 2010-05-01
Actually, not only is it not impossible, it is totally simple to change.

Do this...

Copy the Ambiance theme to your home "./themes" directory. This will be the the config file that is used for your username. This fix will change transparencies on a per user basis, not system-wide. This also preserves the system-wide file so you can't mess it up.

```
cp -R /usr/share/themes/Ambiance ~/.themes/
```

Open the theme file in gedit

```
gedit ~/.themes/Ambiance/gtk-2.0/gtkrc
```

Find this line and coment it out. (with a #)

So

```
bg_pixmap[NORMAL] = "panel_bg.png"
```

becomes

```
# bg_pixmap[NORMAL] = "panel_bg.png"
```

Finally, using System > Preferences > Appearance settings, switch momentarily to another theme, then back to Ambiance and your changes should take effect. 

All credit for this fix goes to [Rebel Zero]("http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244")

Note: If you have made some other changes with gconf-editor, for example restoring the freaking window control buttons to the correct (right) side, you might need to make these changes again. I don't know why that is yet

---

### Post by RazorV on 2010-05-06
Thanks so much ijustwantyourhalf!  That worked Perfectly!  Thanks again!

---

### Post by Raul1800 on 2010-08-12
> **ijustwantyourhalf said:**
> Actually, not only is it not impossible, it is totally simple to change.

Do this...

Copy the Ambiance theme to your home "./themes" directory. This will be the the config file that is used for your username. This fix will change transparencies on a per user basis, not system-wide. This also preserves the system-wide file so you can't mess it up.

```
cp -R /usr/share/themes/Ambiance ~/.themes/
```

Open the theme file in gedit

```
gedit ~/.themes/Ambiance/gtk-2.0/gtkrc
```

Find this line and coment it out. (with a #)

So

```
bg_pixmap[NORMAL] = "panel_bg.png"
```

becomes

```
# bg_pixmap[NORMAL] = "panel_bg.png"
```

Finally, using System > Preferences > Appearance settings, switch momentarily to another theme, then back to Ambiance and your changes should take effect. 

All credit for this fix goes to [Rebel Zero]("http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244")

Note: If you have made some other changes with gconf-editor, for example restoring the freaking window control buttons to the correct (right) side, you might need to make these changes again. I don't know why that is yet
i have a problem with this method and i hope u could plz help me out.......

 to drag the ambiance theme to my home theme directorey is ths a folder i need to create a theme folder in my home directory? and when you do the change in the gtkrc what do you do with the ambiance folder i copied to my home folder. i mean if i change the theme by going into my preferences to another theme and then change it back to the ambiance theme there would be no change since i'm using the theme thats in the /usr/share/theme directory. i'm sorry if this sounds stupid but I'm a complete noob with Ubuntu since i just started using it about a week ago lol. windows sux compared to ubuntu however i wish ubuntu was easier to customize........

---

