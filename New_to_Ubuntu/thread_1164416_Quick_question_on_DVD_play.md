---
title: "Quick question on DVD play"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by stoppage on 2009-05-19
Hi, I'm running Ubuntu 8.04 & my DVD's currently play automatically with „Totem“. I'd like VLC to play same automatically, I never use Totem. Can anybody help me out here please?

---

### Post by Mornedhel on 2009-05-19
In Jaunty, I can open Nautilus, click Edit > Preferences, Media tab, and change the DVD Video option. I seem to remember it was different in Hardy, maybe a Media (Removable Media ?) entry in the System > Preferences or System > Administration main menu ?

---

### Post by stoppage on 2009-05-19
Same here with the media tab, but no entry for VLC...gxine and Totem only

---

### Post by carml on 2009-05-19
You can choose by right-clicking on a file what kind of application to use to open it,if I were you I'd try it with the DVD inserted,maybe it functions I never tried it before.:)

---

### Post by stoppage on 2009-05-19
o.k.,but that only opens app. on click. Found the solution to make VLC auto-start DVD's on insertion here.....
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

DEFAULT DVD PLAYER


UBUNTU FAMILY 8.04+ USERS ONLY


To change the default DVD player to VLC (not Kubuntu, possible issues with Xubuntu), copy and paste this command into the terminal: 

gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to "Places > Computer > Edit > Preferences > Media > DVD Video", and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD. If playback doesn't work properly, navigate to "Video > Deinterlace" within VLC and select mode "Blend". If that still doesn't solve your issue, or you just want more features enabled upon launch (such as fullscreen upon launch), follow the intructions in the next paragraph.

Right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties", and change the launch command from "wxvlc %F" to:

vlc --volume 512 %m

or to have DVD playback automatically launch in fullscreen:

vlc --volume 512 --fullscreen %m

Close the VLC properties dialog and exit the menu editor.

Note: Remember to enable deinterlacing in "VLC > Video > Deinterlace" if you see any artifacts during playback, or if playback doesn't work correctly (the same is true with some AVI files also). To exit and enter fullscreen in VLC, just press the "f" key.

Obliged for the help

---

