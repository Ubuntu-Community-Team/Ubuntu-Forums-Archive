---
title: "wallpaper tray out of control"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by liquidus219 on 2009-10-06
I'm running the beta of karmic koala, and have just installed the wallpaper-tray add-on for the panels. Unfortunately (and quite stupidly) I set the time on the rotation as ".5", so now the wallpaper is changing every .5 of a second.

The only way I can stop it is by stopping the process in the system monitor, as the icon on the panel has disappeared. Could someone please help me open the preferences?

---

### Post by liquidus219 on 2009-10-11
Can someone PLEASE help me correct this?

---

### Post by howefield on 2009-10-11
> **liquidus219 said:**
> Can someone PLEASE help me correct this?

Open Synaptic Package Manager and remove it ?

You had to add the applet manually to the panel in the first place, do it again...

[Edit]Having replicated that, rofl... I'd say your best bet is my first option, remove the package with Synaptic Package Manager, then log out and back in. You should be ok then.

---

### Post by durand on 2009-10-11
If you still want to use it, you can try to find the config folder in your home and delete or edit the config there. Open the filemanager, and go to ~/ in the location bar. Then press Ctrl + H and see if you can find the right folder.

---

### Post by liquidus219 on 2009-10-12
Thanks to everyone - I reinstalled and logged back in but that didn't work. However, I managed to get it working again by going through the gconf-editor.

---

