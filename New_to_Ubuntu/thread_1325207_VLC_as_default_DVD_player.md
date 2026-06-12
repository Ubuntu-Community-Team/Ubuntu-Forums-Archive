---
title: "VLC as default DVD player"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-11-13
how do you set VLC player as default for videos and dvds?

---

### Post by wojox on 2009-11-13
```
sudo cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'
```

---

### Post by LunaticHiatus on 2009-11-13
thanks again

---

### Post by coldReactive on 2009-11-13
> **wojox said:**
> ```
sudo cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'
```

Err... how about something less lazy?

> To change the default DVD player to VLC (not Kubuntu, possible issues with Xubuntu), copy and paste this command into the terminal:

gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to "Places > Computer > Edit > Preferences > Media > DVD Video", and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD. If playback doesn't work properly, navigate to "Video > Deinterlace" within VLC and select mode "Blend". If that still doesn't solve your issue, or you just want more features enabled upon launch (such as fullscreen upon launch), follow the intructions in the next paragraph.

Right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties", and change the launch command from "wxvlc %F" to:

vlc --volume 512 %m

or to have DVD playback automatically launch in fullscreen:

vlc --volume 512 --fullscreen %m

Close the VLC properties dialog and exit the menu editor.

Note: Remember to enable deinterlacing in "VLC > Video > Deinterlace" if you see any artifacts during playback, or if playback doesn't work correctly (the same is true with some AVI files also). To exit and enter fullscreen in VLC, just press the "f" key.

from [http://georgia.ubuntuforums.org/showthread.php?t=766683](http://georgia.ubuntuforums.org/showthread.php?t=766683)

---

