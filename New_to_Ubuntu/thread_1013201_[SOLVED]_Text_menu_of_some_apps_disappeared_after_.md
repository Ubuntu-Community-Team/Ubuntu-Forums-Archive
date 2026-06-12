---
title: "[SOLVED] Text menu of some apps disappeared after Nvidia upgrade"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Joe Soap on 2008-12-16
I'm running Intrepid 8.10 and today I activated the Nvidia driver (Nvidia binary X.Org driver ('version 96' driver)).  After restarting, I opened Open Office and noticed that the menu text has disappeared.  

I've attached a screenshot (OOffice.png) here to show the result. [ATTACH]96629[/ATTACH]

(Not quite sure how the attachment thingy works though ...)

I noticed the same behaviour in K3B and Krita.

Any solutions out there?

---

### Post by Joe Soap on 2008-12-16
Ok, my bad. This is a known bug ([http://www.nvnews.net/vbulletin/showthread.php?t=122350](http://www.nvnews.net/vbulletin/showthread.php?t=122350)).  It occurs if you have visual effects enabled.  Set that to None and everything is ok again.

---

### Post by starcannon on 2008-12-16
If you like your visual effects then a work around that I use is fusion-icon
```
sudo apt-get install fusion-icon
```run fusion-icon from Applications>System Tools>Compiz Fusion Icon
Now anytime your window decorations vanish just r-click the fusion-icon and choose "Reload Window Manager" from the dropdown menu, if all goes as planned you'll have window decorations and text back.

GL and have fun

---

