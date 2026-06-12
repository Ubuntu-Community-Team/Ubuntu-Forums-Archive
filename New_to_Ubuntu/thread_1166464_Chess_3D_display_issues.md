---
title: "Chess 3D display issues"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by NyteMyre on 2009-05-21
OK, so I've been on Ubuntu about a day and a half.  I've installed the requested packages to run Chess in 3D, but the window instantly closes without so much as an error box.  I'm using a graphics card that I'm not entirely sure Ubuntu is capable of being friendly with (I spent pretty much all of yesterday repenting for my attemps at installing various versions of xorg, and in the end, ended up having to format because even vesa compatability mode wouldn't boot to anything other than a root prompt).   It's an radeon mobility x600, and unfortunately almost all information regarding that is circa 2005, where it seems all the forums I've searched have developed magical fixes for the xorg.conf file that do nada for me.  I'm not sure whether I should just sit on the xorgr version already installed or keep trying to get ati's esoteric .run file to install what's probably a more dated version of the xorg drivers (not that I know how to find out what's right), but for what it's worth, glxgears runs fine, I'm just unsure I'll ever be able to run anything more advanced. >_<

Anyway, Ubuntu is driving me nuts.  I love it because I've never seen such ease of installation and it all feels so smooth when I get it right, but I'm suffering a flurry of defeats.

I'll settle for getting Chess back into 2D mode.  I'll write up a detailed post about the graphics in another post if it can't be helped with what little I've said.

---

### Post by 67GTA on 2009-05-21
It's not you. There is a Gnome bug in the current chess game version. It has something to do with opengl. I doubt it will get fixed until Gnome 2.27. I would recommend brutal chess. It is installable through the package manager, and is 3D.

---

### Post by Rhubarb on 2009-05-22
Unfortunately it's a known python-opengl bug affecting Ubuntu 9.04 (Jaunty):-
[https://bugs.launchpad.net/gnome-games/+bug/350850](https://bugs.launchpad.net/gnome-games/+bug/350850)

---

### Post by Arup on 2009-05-24
sudo apt-get install brutalchess

Works nice in 3d mode.

---

