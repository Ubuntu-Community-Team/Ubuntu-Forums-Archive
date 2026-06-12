---
title: "Root Window"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2010-01-09
How do I send VLC's video output to the root window (desktop background)? I'm trying to have a video play as a wallpaper behind the icons and stuff and replace the desktop image I have now.

---

### Post by sisco311 on 2010-01-09
[http://blogs.law.harvard.edu/hoanga/2008/02/06/how-to-play-mplayer-in-the-desktop-fullscreen-on-ubuntu/]("http://blogs.law.harvard.edu/hoanga/2008/02/06/how-to-play-mplayer-in-the-desktop-fullscreen-on-ubuntu/")

---

### Post by Sup3r3g0 on 2010-01-09
I followed the code you linked to. 
```
# Tell GNOME to not handle the desktop
$ gconftool-2 &#8211;type bool &#8211;set /apps/nautilus/preferences/show_desktop false
# Play a video file in the rootwin as fullscreen
$ mplayer -rootwin -fs my_cool_video.avi 
```
But then I got this. What happened?
```
X11 error: BadMatch (invalid parameter attributes)
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
```

And how do I know if the first command worked and turned released Gnome's control of the desktop? Should the wallpaper and my icons be blank, because if so, the command didn't work.

---

