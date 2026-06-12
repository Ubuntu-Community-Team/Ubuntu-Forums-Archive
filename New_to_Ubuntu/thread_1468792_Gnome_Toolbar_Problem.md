---
title: "Gnome Toolbar Problem"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by kiplingw on 2010-05-01
Hey everyone. There use to be a GUI in Gnome in System -> Preferences -> Menus & Toolbars to change the toolbar preferences to show just icons, just text, or both. I am running Lucid now and I can't seem to find it.

---

### Post by mikewhatever on 2010-05-01
System->Preferences->Appearance, the 'Interface' tab.

---

### Post by kiplingw on 2010-05-01
No interface tab visible. I am running Lucid. Did they strip it?

---

### Post by mikewhatever on 2010-05-01
Possibly. What tabs are there?

---

### Post by kiplingw on 2010-05-01
{ Theme, Background, Fonts, Visual Effects }

:confused:

---

### Post by ankspo71 on 2010-05-01
Hi, Open the Gnome Configuration Editor by pressing Alt+F2 and typing gconf-editor, then navigate to:
/desktop/gnome/interface/toolbar_style
then edit the option.
Note: Valid values are "both", "both-horiz", "icons", and "text".

---

### Post by kiplingw on 2010-05-01
Thanks. Very strange that the Interfaces tab is gone though.

---

