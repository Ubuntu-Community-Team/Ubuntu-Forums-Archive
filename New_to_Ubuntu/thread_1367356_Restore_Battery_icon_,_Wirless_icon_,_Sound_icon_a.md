---
title: "Restore Battery icon , Wirless icon , Sound icon and the Bluetooth icon ubuntu 9.10"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by s0ulkeeper on 2009-12-29
i got the battery icon  wireless icon and sound icon to restore , but they look different and the bluetooth icon i cant seem to get that to come back
how do i move those icons around  in the tray , like how i move icons in the panel ..

using ubuntu 9.10

---

### Post by HarrisonNapper on 2009-12-29
Those icons are all part of the notification area. You can only move them as a whole on the panel (by default). Are you using a laptop? There may be a soft switch on your computer to activate/deactivate bluetooth. Try installing blueman ```
sudo apt-get install blueman
``` and see if that works.

---

### Post by tom.swartz07 on 2009-12-29
> **HarrisonNapper said:**
> Those icons are all part of the notification area. You can only move them as a whole on the panel (be default). Are you using a laptop? There may be a soft switch on your computer to activate/deactivate bluetooth. Try installing blueman ```
sudo apt-get install blueman
``` and see if that works.

I dont think that's the problem.

It sounds like you accidentally deleted your notification applet.

Put your mouse over the panel bar that you are missing the icons from, right click.
go to 'add to panel' and select notification applet from the list.

That should restore it!


Unfortunately, you cant organize how they appear in the notification area. They are listed in the order that they are launched or created when you log in.

---

### Post by s0ulkeeper on 2009-12-29
i was able to get those back , but they dont look right , the battery icon is all gray and no color at all
those 3 icons move only as a set like u said :|

---

### Post by Subiono Ahmad on 2009-12-30
how bout this :
gconftool –recursive-unset /apps/panel
 
then,type this to delete current one:
rm -rf ~/.gconf/apps/panel

Finally,reload panel:
pkill gnome-panel

end your session then go to Panel > Add panel > Add Notification

---

