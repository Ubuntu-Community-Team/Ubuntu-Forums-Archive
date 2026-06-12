---
title: "A few problems"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by jacob_pikachu on 2010-01-26
Hey everyone, my third day on UNR (and Ubuntu in general).

So I got all of the silly UNR interface issues worked out and back to standard desktop.  Also wifi and all of my special buttons are working properly.

A few issues that I need some help addressing are:

-Screen does not lock on resume from standby.
-wifi does not work on resume from standby (it does work after a system restart)
-ctrl+click does not open links in new tab in firefox or chromium

Thanks in advance for any help

-Jacob

---

### Post by Rayve on 2010-01-26
What netbook are you using?  I have a System76 that had an issue with wifi, ultimately I had to enter: ```
 sudo dhclient wlan0 
``` in a terminal to get my wifi connected after a standby/boot up.  

You may want to browse around the System76 forums here to see if others with netbooks (I think the main/only one for System76 is the Starling) have similar issues and were able to find a work around.  Even if yours isn't from System76, chances are that'll be your greatest population of Ubuntu Netbook Remix users.  :)

---

### Post by jacob_pikachu on 2010-01-26
I am using an eeepc 1008ha

---

### Post by Rayve on 2010-01-26
I have the same problem with Ctrl+Click not opening a new tab in Firefox when using my netbook, but I just right-click and choose open in new tab.  I suspect it has something to do with using a touchpad versus an actual mouse and assume there's a workaround, possibly a setting in UNR or Firefox itself, beyond just getting a usb mouse.

---

