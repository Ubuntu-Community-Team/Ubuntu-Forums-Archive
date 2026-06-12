---
title: "Emerald Themes?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Sly-.- on 2009-08-26
Hey all. I'm using 9.04, and have emerald and compiz ready to be used, I imported my theme into the emerald theme manager, but I don't see any way of activiating these themes. Anyone want to kindly tell me how to do so?

Thanks. :)

---

### Post by tuxxy on 2009-08-26
Open your Emerald window and drag the .tar.gz theme file into the open Emerald window, this will install the theme and then to select the one you would like to use simply click on the new theme which appears in the list.  

When you click on the different themes in Emerald if your window title-bars do not change then you may need to load emerald as you could still be using metacity.  To solve this press ALT + F2 and a window will appear, in this window paste the following command and hit enter.
```

emerald --replace
```Now you should see your emerald theme, once you reboot your system though it may return back to metacity as default Window Manager so to prevent this happening and you having to run that command at every boot you could add it to your startup applications located at system > prefs > startup apps

---

### Post by Sly-.- on 2009-08-26
Thanks thats great mate. And say I delete all my emerald themes and want the window to change back to the default of the GTK theme I'm using, how do I do so?

Thanks again

EDIT: Nevermind, used some good ol' common sense. :P Thanks again mate.

---

### Post by tuxxy on 2009-08-26
If you want to revert back to Metacity (the default) you dont need to delete the emerald themes.  Just load it backup like you did with emerald.  So ALT + F2 and then enter this;

```
metacity --replace
```

Although if you added the original emerald --replace command to your startup applications then you wont need to do this, you can just disable that command in your startup applications and Emerald will not load at boot.  

Also if you have time maybe have a look at compiz fusion-icon available in the repos.  This will sit on your taskbar and has a menu that allows you to change from emerald to metacity window managers by simply clicking on it. :D

---

