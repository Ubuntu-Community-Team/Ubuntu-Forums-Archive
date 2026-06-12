---
title: "Top Bar - lost the menu words"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Chalfont on 2009-05-28
Top Bar - lost the menu words.
Hi
I am sure this is so simple and yet I cannot find what to do.

Somehow, while playing around with the look and feel of the menu bar thingy at the top, I have lost the three menu items.  The little circle graphic is still there.

How do I get the words back without reinstalling the whole of Ubuntu from scratch?

** Please do not assume I know how to find something - if you have a suggestion, please tell me how to do it, step by step, from the basic screen (minus the menus LOL!) 

Thanks

---

### Post by pastalavista on 2009-05-28
If you right-click on the panel and select "Add to panel", you'll see a list of apps that you can add. There are two "menu" selections. The "Menu Bar" is the one with the words "Applications, Places, System" and the "Main Menu" has just the Ubuntu icon and the menu categories drop down. Add the one you want and remove the one you don't. If items are missing, you can right click the menus bar and select "Edit menu" and customize which applications are in the lists.

---

### Post by Chalfont on 2009-05-28
Cool, Thanks

---

### Post by RD1 on 2009-05-28
You apparently removed the "Menu Bar" and added the "Main Menu" applet to the panel.

Right click on an empty space on the panel and select "Add To Panel". Scroll down and select "Menu Bar" then click "Add". Close the "Add To Panel" window.

Right click on the lone "circle graphic" and select "Remove From Panel". You can drag the "Menu Bar" into the preferred position then right click on it and select "Lock To Panel"

Good Luck

---

### Post by nothingspecial on 2009-05-28
If you click on the ubuntu logo thingy your menus should be there.

I think it looks nicer but it`s up to you.

---

### Post by drs305 on 2009-05-28
One more tip, although the previous posts should restore the menu bar which is what you wanted: If you want to restore the panels entirely to the default settings, you can do so by removing or renaming the gconf panel settings folder. 

The following command will rename the existing panel folder rather than delete it so you can restore it if you don't like the new result:
```

mv $HOME/.gconf/apps/panel $HOME/.gconf/apps/panel-old 
sudo /etc/init.d/dbus restart

```
If the restart command causes any problems, just reboot. A new default "panel" folder will be created with the original panel settings.

---

### Post by Chalfont on 2009-05-28
Thanks

Can anyone else validate this code as OK please before I run it?

---

### Post by nothingspecial on 2009-05-28
Yep. That`s backing up your old configuration before going back to the default.  No worries there.

---

