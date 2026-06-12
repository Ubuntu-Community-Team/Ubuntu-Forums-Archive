---
title: "Effects help!!!!"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2009-09-13
Ok, so I hear and see that compiz fusion is awesome! So I want to activate my effects to get the best out of Ubuntu, plus I'm told that my version of Ubuntu has Compiz Fusion built-in. Anyway, whenever I try to turn on my effects, Ubuntu says it won't work. I have no idea why. I used Wubi to install Ubuntu if that helps. Anyway, please help, because I'm a total noob an nobody I knows uses Ubuntu :(

Also, if this won't activate compiz fusion, please help me know where to get it

---

### Post by jbrown96 on 2009-09-13
You probably don't have the graphics drivers installed. System--->Administration--->Hardware drivers. See if there is anything there. You will need to reboot after you install. If you can get the compiz working, you will also want the compizconfig-settings-manager ```
sudo apt-get install compizconfig-settings-manager
``` This will give you a bunch more plugins to use. 

To use it, first go to system--->preferences--->appearance, then visual effects tab and set to custom. Then open the settings manager in system--->preferences.

---

### Post by ankspo71 on 2009-09-13
If there is no graphics card driver listed in your Hardware Manager. You can still get 'some' 3D effects. I don't think it requires a 3D graphics driver either.

You will have to enable the compositing-manager in the configuation manager.
to do that, simply type this in a terminal window:

```
gconf-editor
```

Then go to Apps> Metacity> General>...
Then look for "compositing-manager" and put a check mark by it.

The will allow some transparency (like for cairo-dock, etc) and give you some shadows on the desktop. It wouldn't give you everything like compiz would but it's good to have if you don't have a 3D graphics driver available (I think).

James.

---

