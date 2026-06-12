---
title: "Identify GNOME Window on Command Line"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by djmoore on 2009-08-11
Is there a way to identify a gnome window on the command line, or at least to list the open windows?

I want to use this in connection with scrot (or similar) to take screenshots.

I'll appreciate any insight.

---

### Post by lykeion on 2009-08-11
Ok, there maybe a simpler solution but after checking this thread [http://ubuntuforums.org/showthread.php?t=893323]("http://ubuntuforums.org/showthread.php?t=893323") I could get a screenshot for a specific window from command line without using the mouse.

You will need to have these packages installed: x11-utils xdotool imagemagick

To get the id of the window you can use the xwininfo command like this:
```
xwininfo -name "Window Title" | grep xwininfo | cut -d ' ' -f 4
```

Then we need to activate the window and take the screenshot like this:
```
xdotool windowactivate <ID> && import -window <ID> screenshot.png
```

So for example if you want to take a screenshot of the window with title "Mozilla Firefox" and save this to the file screenshot.png you can achieve this with:
```
ID=$(xwininfo -name "Mozilla Firefox"|grep xwininfo|cut -d ' ' -f 4);xdotool windowactivate $ID && import -window $ID screenshot.png
```

Of course it would be simpler to make this into a bash script...

---

### Post by kaibob on 2009-08-11
> **djmoore said:**
> Is there a way to identify a gnome window on the command line, or at least to list the open windows?...

I do not know much about this topic, but wmctrl will list open windows:

```
wmctrl -l
```

An example of output:

> kaibob@dell:~$ wmctrl -l
0x01200003 -1 dell Bottom Expanded Edge Panel
0x01200026 -1 dell Top Expanded Edge Panel
0x01a0001c -1 dell x-nautilus-desktop
0x02200038  0 dell [gnome] Identify GNOME Window on Command Line - Ubuntu Forums - Shiretoko
0x02400003  0 dell notes
0x01a0096f  0 dell autosave - File Browser
0x02600003  0 dell bash.ncd - NoteCase 1.9.8 [/home/kaibob/documents/notecase/bash.ncd]
0x02800004  0 dell kaibob@dell: ~

---

