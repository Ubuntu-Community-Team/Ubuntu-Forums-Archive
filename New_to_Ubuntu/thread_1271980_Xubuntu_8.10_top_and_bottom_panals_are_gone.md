---
title: "Xubuntu 8.10 top and bottom panals are gone"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Ewingo401 on 2009-09-21
Hey guys.  I'm working on my brothers computer which is running Xubuntu 8.10 at the moment.  Both the top and bottom menu panels have dissapeared and I have no idea how to get them back.  I had to Alt+F2 just to be able to launch firefox.  Any ideas?

---

### Post by sisco311 on 2009-09-21
Press Alt+F2 and type: xfce4-panel

If the panels are showing up, then go to Menu -> Settings -> Session and Startup -> Session tab and change the *Restart Style* of xfce4-panel to *Immediately*.

If not, then try to reset the default panels by deleting/renaming the ~/.config/xfce4/panel directory. Press Alt+F2, type thunar, press Ctrl+H to list hidden files, navigate to .config/xfce4... Then try to launch the panel again.

---

### Post by Ewingo401 on 2009-09-21
That fixed it.  Thank you very much!

---

