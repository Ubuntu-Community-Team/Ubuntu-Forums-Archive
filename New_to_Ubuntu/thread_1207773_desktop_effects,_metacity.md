---
title: "desktop effects, metacity"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-07-08
I was playing around with compiz in Intrepid and couldn't get all the annoying effects turned off so i uninstalled compiz through SPM and for good measure reinstalled metacity, however i can't seem to get metacity enabled as a desktop manager and my windows are all screwy again. couldn't find the terminal commands to set things right again.

---

### Post by alexlafreniere on 2009-07-08
So what you're saying is Compiz is still set as your window manager even though it is uninstalled? If not, what is your window manager? If you have a GUI, then Metacity is still working.

---

### Post by Messyhair42 on 2009-07-08
then something isn't configured correctly. I can't use my "hide windows, show desktop" buttong and windows like firefox cover the upper taskbar, also i dont get buttons showing what's running in the lower taskbar.

Edit in responce to Sealbhach (below): visual effects are off and the whole pane is greyed out, probably because i dont have compositing enabled through either compiz or metacity

---

### Post by Sealbhach on 2009-07-08
You can turn off visual effects in System/Preferences/Appearance (see screenshot). You could also install the Compiz Fusion icon to easily switch window managers (handy if you play games).

.

---

### Post by JOHNNYG713 on 2009-07-08
Maybe there is a better way; but I would reinstall compiz and the "compiz-fusion icon, after re-installation goto applications system tools and click compiz fusion icon this will place a icon in your launcher panel  (in alert area) right click that select window manager "metacity"
And try not to take such drastick measures:guitar:
And allways back up your home folder!

---

### Post by Sealbhach on 2009-07-08
> **Messyhair42 said:**
> then something isn't configured correctly. I can't use my "hide windows, show desktop" buttong and windows like firefox cover the upper taskbar, also i dont get buttons showing what's running in the lower taskbar.

Try this. Right-click on the panel and add Window Selector and Show Desktop.

If you need to move an open window lower down, click Alt+Right Mouse Button and drag it to where you can see it.

Hope this helps.

.

---

### Post by Messyhair42 on 2009-07-08
> **JOHNNYG713 said:**
> Maybe there is a better way; but I would reinstall compiz and the "compiz-fusion icon, after re-installation goto applications system tools and click compiz fusion icon this will place a icon in your launcher panel  (in alert area) right click that select window manager "metacity"

solved! thank you.

---

### Post by sam_delta on 2009-07-08
you can enable metacity composite, i duno if thats the problem, but anyways, you can try it

open a terminal and type ```
gconf-editor
``` then on gconf, on the left side, navigate through apps>metacity>general, and after selecting "general" folder, on the right side search for "composition_manager", and check it

sam

---

