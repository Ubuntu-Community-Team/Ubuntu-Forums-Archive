---
title: "Missing window borders and decorations"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by sturdy on 2011-07-27
Hi all,
When I boot I have no window decorations, top title bar or window borders, and other strange behavior with the classic desktop. It seems to be a compiz issue. If I exec compiz --replace, the missing windows items are replaced but fails again on reboot. Also I get a debug msg that indicates compiz can't find a .compiz-1/plug-ins directory. That dir is not present. I have installed plugins and re-installed compiz but no help.

Any ideas? Thanks in advance.

---

### Post by sledge73 on 2011-07-27
If executing compiz --replace works you can write a script like
```

!#/bin/bash

sleep 5 && compiz --replace;

```

What you name it is not important, just remember the name.
Place it in your home folder make it executable & add to startup applications.
Then reboot.
Thats a good temp solution until you can find the cause.

---

### Post by sturdy on 2011-07-27
Thanks sledge73 but I would really like to find a fix...:)

---

### Post by zathras1974 on 2011-07-27
First off, deep breath. This is a common issue. 

Lemme guess, the problem started right after you tried to enable desktop cube, right? If so, there is an [excellent how-to]("http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html") over at Ubuntu4Beginners. Just follow the steps and you should have your decorations and bars back in no time. :)

---

### Post by CatKiller on 2011-07-27
```
compiz-decorator --replace
``` is probably sufficient, rather than reloading the whole window manager.

> **sturdy said:**
> Also I get a debug msg that indicates compiz can't find a .compiz-1/plug-ins directory.

That looks like part of a GConf tree. I don't know what would cause that to not be there on a properly configured Compiz install.

---

### Post by Frogs Hair on 2011-07-27
If you can't access a terminal you can try to reset Compiz from the recovery console with the following command .```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot

```

---

### Post by sturdy on 2011-07-27
Well...first, thanks to all for responding. Unfortunately, I have tried all suggestions and nothing solves the problem. Here is the rest of the story...

I installed Natty when first released. At the time I noticed the title bar was missing and windows were erratic, etc. but I thought it was a problem with the Natty release and would be fixed. So I used Unity until yesterday when I woke the computer from hibernation and the Unity desktop was unusable. I am unable to access anything in Unity, icons are all very large and dead, alt-F2 is inop, etc. So I returned to the classic desktop and discovered that all is good when I right click the Compiz Fusion Icon and select Reload Windows Manager or click Compiz at Select Windows Manager. I also set Notification to Debug in the Compiz Utility menu. I have installed Compiz plugins but Compiz tells me each time I restart the WM that it cannot locate the plugin files in ~/compiz-1/plugins/filename. The plugin dir is missing.

This seems to be a config issue. If I could reset the config or delete the WM config files all would probably return to close to normal. It's like after startup the WM starts from a defective config and when I restart Compiz it uses a valid config. there is no joy in Mudville tonight...

---

### Post by CatKiller on 2011-07-28
> **sturdy said:**
> Compiz tells me each time I restart the WM that it cannot locate the plugin files in ~/compiz-1/plugins/filename.

Are you sure it says ~/compiz-1? There's no reason why anything should be there.

> 
This seems to be a config issue. If I could reset the config

That's what the --recursive-unset option does. Although doing it from recovery mode would potentially do it as the wrong user. Doing it from a normal Terminal, or Ctrl-Alt-F1 to get to a virtual console, would probably be more likely to work.

---

### Post by sturdy on 2011-07-28
I don't know why but my Unity desktop is back (magic!). Still the same issues with Classic but I can live like this, at least for now. I don't understand the .compiz-1/plug-ins folder. It seems I have a .compiz (Unity) and a .compiz-1 (Classic) folder for each WM. But neither has a plug-ins subfolder. However, there is a 'sessions' subfolder in each. At least I'm operational again (using Unity) so will consider this resolved until I can find the real issue. Thanks to all ... take care.

---

