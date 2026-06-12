---
title: "WINE not properly running program"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by Greendolph on 2011-06-25
I am trying to run a program called 'Roblox' on Ubuntu using WINE. Roblox is a 3D game design environment.

When roblox opens normally, it brings up a 'configuring roblox' message box if roblox is being updated or needs configured on a new system. After that- it closes that dialog box and bricks up a 'starting roblox' box with a side scrolling progress bar. When that application is complete the roblox studio opens. 

In Ubuntu however studio never opens. Every time I open a roblox file or roblox studio it goes through the configuration and update stage and then the 'starting roblox' box. But the application disappears after that. 

When I try opening a rbxl (roblox) file using terminal I get this:

kelson@ubuntu:~$ wine "/home/kelson/corn.rbxl/"
wine: Bad EXE format for Z:\home\kelson\corn.rbxl\.


Does anyone have any experience with this sort of problem? Your help is very appreciated.

---

### Post by Ozymandias_117 on 2011-06-25
You can find information about Wine applications at [http://appdb.winehq.org/](http://appdb.winehq.org/)

After searching for it on there, users say > In order to get Roblox working, you will need to install ie7 and wmp10 via winetricks. The browser plugin doesn't work, and it is a pain to log in. You can still use the studio to build.

So, it may or may not do what you want, but that might at least get you further.

---

### Post by Greendolph on 2011-06-25
Thank you. I will look into that.

---

### Post by Gorillabond on 2011-09-23
Face it Wine isnt perfect...You cant run all Windows apps on Wine...Especially those 3D ones..Graphic Driver incompatibilites.

---

