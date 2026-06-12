---
title: "Problem with Gnome Panel"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-04-06
I am having a small problem. I can not seem to get rid of the sides of the panel. I would like to get rid of them, but I can't find out how. I would like to make it look like the second picture. The first is mine by the way.

---

### Post by nandemonai on 2009-04-06
> **slughappy1 said:**
> I am having a small problem. I can not seem to get rid of the sides of the panel. I would like to get rid of them, but I can't find out how. I would like to make it look like the second picture. The first is mine by the way.

Right click the panel -> properties -> uncheck 'show hide buttons'

---

### Post by mcduck on 2009-04-06
That's not possible, the panel handles are hard coded feature of Gnome-panel (there is no gnome-panel running in the second screenshot).

There is a trick to hide handles for Window List- and Notification Area-applets, by replacing them with fully transparent image. But the handles at panel ends are there to stay, unless you are able to rewrite the gnome-panel's code to work without them.

---

### Post by slughappy1 on 2009-04-06
It is unchecked already. 

So how do you think I can get a panel that looks like the other picture?

---

### Post by JK3mp on 2009-04-06
i disagree I DO see a gnome panel in the second image, bottom right hand corner, there also running gnome-do docky but thats not what he's reffering to. As for the handles option, perhaps you can just make the panel 100 percent transparent, but use a theme set or color scheme that still shows the menu part.

---

### Post by nandemonai on 2009-04-06
Ah right, shows what I know :P

---

### Post by slughappy1 on 2009-05-18
So I found out this is how to disable the gnome-panel, taken from [http://wiki.awn-project.org/FAQ#How_do_I_permanently_remove_GNOME_Panel_from_my_GNOME_session.3F](http://wiki.awn-project.org/FAQ#How_do_I_permanently_remove_GNOME_Panel_from_my_GNOME_session.3F)

**[SIZE="3"]How do I permanently remove GNOME Panel from my GNOME session?[/SIZE]**
Note: Depending on the version of GNOME installed, there are different instructions. Please pay attention to the bolded version numbers.

For versions of GNOME up to version 2.22, you need to Open the "Sessions Preferences" dialog, found at System &#8594; Preferences &#8594; Sessions. Click on the "Current Session" tab, select the "gnome-panel" entry, press the "Remove" button, and then press the "Apply" button. Then, to make sure that the session remembers not to start gnome-panel at startup again, close all of the programs that you do not wish to run at startup except the Sessions Preferences dialog, click on its "Session Options" tab, and press the "Remember Currently Running Applications" button.

For versions of GNOME after version 2.22 (for example, Ubuntu Intrepid and later, or Fedora 10 and later), there are two options.

If you have "Configuration Editor" (AKA gconf-editor) installed, run it and navigate to the key folder /desktop/gnome/session. Double-click on the key required_components_list in the right-hand pane to edit it, and remove the value "panel" by selecting it and pressing the "Remove" button, followed by the "OK" button.

Alternatively, you can run the following command from the terminal:

gconftool-2 --type=list --list-type=string --set /desktop/gnome/session/required_components_list '[windowmanager,filemanager]'

With either method, for the changes to be applied, you need to log out and log back in.

---

### Post by nothingspecial on 2009-05-18
I just move gnome-panel out of /usr/bin/. Job done.

However you can hide it completely. The default hide size is 6 which means when you choose auto hide you can still see the top (or bottom) of the panel at the edge of your screen.

If you launch gconf-editor an go apps > panel > top levels you can change the autohide size to 1 which makes it disappear completely. The advantage is that you can still call your menu with Alt F1 and you can still have those funky new notifications.

---

### Post by Liova99 on 2011-04-03
> **nandemonai said:**
> Right click the panel -> properties -> uncheck 'show hide buttons'

Thanks!! this work for me on ububtu 10.10.=D>

---

