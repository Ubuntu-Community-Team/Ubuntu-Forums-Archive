---
title: "Deleted Gnome main panel in error and can't get it back"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Buster95 on 2011-04-20
I thought I was deleting an icon on the Gnome main panel and somehow stupidly deleted the whole damned panel. Now I can't get the panel back the way it was.

So far, I have managed to get a panel back and to populate it to some extent. However, I haven't been able to replace the "Places" and "System" menu trees to as-installed. I have to access them via the main pull-down.

Additionally, the Skype "green tick" icon has gone and I can't work out how to get it back. Consequently, there appears to be no way to shut Skype down except by "kill-all" from a terminal.

Any suggestions?

---

### Post by ububeginner on 2011-04-20
There are two menu items in the add to panel pop up, the "menu bar" should contain applications, places and system by default. you can also right click on it and select "edit menus" to customise it.

As for the skype, I don't know. Have you tried "indicator applet"?

---

### Post by dcsoldschool53 on 2011-04-20
[B]This command restores the Gnome panel back to it's default settings.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```but what you also need to learn to do, is save your Gnome panel setting as a file. Then, reloading it when you mess it up. If you need that info, you will have to start a new thread.
[/B]

---

### Post by Buster95 on 2011-04-21
> **ububeginner said:**
> There are two menu items in the add to panel pop up, the "menu bar" should contain applications, places and system by default. you can also right click on it and select "edit menus" to customise it.

As for the skype, I don't know. Have you tried "indicator applet"?

Thanks,
I actually did load the Gnome menu precisely as you suggested, but it only loaded the "Applications" pull-down, not the others. I have also looked at the edit option, but can't see how it can help me to return the two missing items.

Regarding Skype, I already have the indicator applet loaded. The "green tick" doesn't seem to be associated. I will try removing and reloading Skype to see if something miraculous occurs.
Cheers
Cheers

---

### Post by Buster95 on 2011-04-21
> **dcsoldschool53 said:**
> [B]This command restores the Gnome panel back to it's default settings.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```but what you also need to learn to do, is save your Gnome panel setting as a file. Then, reloading it when you mess it up. If you need that info, you will have to start a new thread.
[/B]

Thanks for this suggestion.
I tried it but it reloaded the current Gnome panel, not the default one.
Cheers

---

