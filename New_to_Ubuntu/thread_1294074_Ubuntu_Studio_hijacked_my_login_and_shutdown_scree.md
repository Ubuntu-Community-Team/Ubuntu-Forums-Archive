---
title: "Ubuntu Studio hijacked my login and shutdown screens"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by Vined Adobo on 2009-10-17
I just installed Ubuntu Studio.  It really screwed up my desktop and Firefox.  I liked my old 9.04 login screen and shut down screen and my old firefox theme, but Ubuntu Studio hijacked them and installed its own idea of what my computer should look like.  It changed the logo on my applications bar on the top of my desktop.  It replaced the theme on Firefox.  I have problems with my eyesight.  Ubuntu Studio made all of the labels on all the tool bars so small, I can't read them without getting right next to the screen.  You may say, "Use view to zoom in," but alas, the  toolbars do not zoom.  I can't see what page I am on, or see why I may have made a mistake in typing the URL.  The fonts on the toolbars on the desktop and the programs running in the program tray do the same. I can't even read the temperature without holding the laptop up to my nose.  I tried to go back to my Tango! theme in firefox, but it is grayed out and can't be selected.  Can anyone help me to get back my old desktop and firefox settings?

Thank you all in advance!
Dave

---

### Post by Devon64327 on 2009-10-17
HEHE... hijacked... Have you uninstalled Ubuntu studio? Did you ever save your preferences? can you revert? If none of these work U may have to find a new theme and  just install that... 





What is wrong with the default that comes with it? All i changed was my background i love the rest




Sorry im a little new to linux and Im just bored going around beginner forum

---

### Post by ad_267 on 2009-10-17
You can probably remove most of it with:
```
sudo apt-get purge ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-gdm-theme ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme ubuntustudio-wallpapers
```

---

### Post by Vined Adobo on 2009-10-17
Thank you!  This worked perfectly!  Everything is as it was.

Thanks again
Dave

> **ad_267 said:**
> You can probably remove most of it with:
```
sudo apt-get purge ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-gdm-theme ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme ubuntustudio-wallpapers
```

---

