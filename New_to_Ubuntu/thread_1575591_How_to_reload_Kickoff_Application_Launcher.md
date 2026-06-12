---
title: "How to reload Kickoff Application Launcher"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Scifer on 2010-09-16
I installed new software in Lucid Lynx but it's icon doesn't appear. How do I reload Kickoff?

---

### Post by utnubuuser on 2010-09-16
Alt-F2 then type kickoff and click run

You can also make a launcher for it by right-clicking the top panel, selecting "Add to Panel" then "Custom application launcher", click "Add", then enter "kickoff" in the pop-up for the command (command might have to be /usr/bin/kickoff instead of just kickoff). When the launcher is created on the panel, you can right-click it again, select properties, then click on the icon to change the icon to whatever icon you want to use for it.

---

### Post by Scifer on 2010-09-16
> **utnubuuser said:**
> Alt-F2 then type kickoff and click run

You can also make a launcher for it by right-clicking the top panel, selecting "Add to Panel" then "Custom application launcher", click "Add", then enter "kickoff" in the pop-up for the command (command might have to be /usr/bin/kickoff instead of just kickoff). When the launcher is created on the panel, you can right-click it again, select properties, then click on the icon to change the icon to whatever icon you want to use for it.
There is no kickoff in my system.
```
sudo find / -iname '*kickoff*'
/usr/lib/libkickoff.so
/usr/share/kde4/apps/desktoptheme/oxygen/dialogs/kickoff.svgz
/usr/share/kde4/apps/desktoptheme/default/dialogs/kickoff.svgz
/usr/share/kubuntu-default-settings/kde4-profile/default/share/config/kickoffrc
/home/scifer/.kde/share/config/kickoffrc
```

---

