---
title: "FF Menus Suddenly Stopped Working?"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by mapes12 on 2010-08-21
Everything was fine then yesterday I had an Update Manager notification to update the Linux header to 2.6.(something or other). Now today I fired up my Thinkpad T23 and none of the menu's in FF respond i.e. File Edit View History Bookmarks Tools Help

No other apps are affected, only FF.

Anyone else had this and how do you fix it?

Mark

---

### Post by jtarin on 2010-08-21
When you boot your Grub menu choose an older kernel and see if that does a fix. A kernel upgrade is not essential if you already have a working configuration. The only reason to actually upgrade is that your missing some feature for newly installed software or hardware.

---

### Post by Rubi1200 on 2010-08-21
Take a look here and see if there is something that might help:

[http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)

(courtesy of forum member lovinglinux)

---

### Post by mapes12 on 2010-08-21
Thanks guys.

Fixed it like this:-

```
firefox -safe-mode
```Select "Reset Tools and Controls" from the pop up. "OK" into Safe Mode, then restart FF in normal mode and all is working again.

:lolflag:

---

