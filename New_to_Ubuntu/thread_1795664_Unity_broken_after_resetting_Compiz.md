---
title: "Unity broken after resetting Compiz"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by jermza on 2011-07-03
So I upgraded 10.10 to 11.04.  It all booted fine, albeit a bit funky here and there.  I then opened Compiz and reset the settings to default.  Suddenly, the left and top panels vanished and won't come back, no matter how many times I restart.  There is nothing but a wallpaper in front of me.  So I have to resort to logging in as "classic" in order to access my menus.

What's going on and how do I fix it?

---

### Post by Ctrl-Alt-F1 on 2011-07-03
Unity is a plugin for compiz.  I'm sure that by setting it to default you disable the plugin.  If you have compizconfig-settings-manager (ccsm) installed open it up and try activating the Ubuntu Unity Plugin.

If you don't have CCSM installed.  The following command will install it:

> sudo apt-get install compizconfig-settings-manager

Edit:  See if alt-f2 works.  You'll need something to type a command into.

---

### Post by jermza on 2011-07-03
The Unity setting was disabled after I reset Compiz, but no menus / panels load on reboot, still.  I've enabled the Unity setting in Compiz.  I have to ctrl-alt-del to restart and choose "classic" to be able to, at least, open my internet browser.

Then, in classic mode, the Unity menu appears on the left and top, AS WELL AS my classic menu structure.  Its just a huge mess in classic mode and absolutely nothing in Unity mode.

I'm not sure what to do...

---

### Post by jermza on 2011-07-03
Got it.

There was a setting in Compiz that had changed from "unity" to "default".  I changed it back to "unity" and it seems to be fine now.

---

### Post by ucracker on 2011-10-16
Thank you for your replay, jermza. It solved my problem aswell.
Just runned terminal (CTRL-ALT-T), wrote ccms, searched for unity, activated it (appeared some dependencies, always pressed the green button). And now it's working.

---

