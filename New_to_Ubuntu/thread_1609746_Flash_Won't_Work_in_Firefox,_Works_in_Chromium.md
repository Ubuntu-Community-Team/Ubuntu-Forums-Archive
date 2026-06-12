---
title: "Flash Won't Work in Firefox, Works in Chromium"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by onaridge on 2010-10-30
In Chromium, without installing anything, flash works. In Firefox, I am prompted to download and install flash. I went to the Software Center and installed it from there. Browser behaves as if Flash was never installed. This is on my laptop with Ubuntu 10.10 installed. Just curious why, Chromium is my browser of choice anyway.

---

### Post by lovinglinux on 2010-10-30
Flash works in Chrome/Chromium because they distribute the plugin along with the browser, which probably won't happen with Firefox.

Due to the proprietary nature of Flash, Ubuntu installs, by default, the open source alternative known as Gnash. Problem is that Gnash is not recognized by some sites and even if you install flash from Adobe, Gnash gets loaded first, causing the error messages you are receiving.

To remove Gnash and other possible conflicting plugins and install Flash from Adobe in Firefox, you can use my extension [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/"). This will solve your problem.

---

### Post by onaridge on 2010-11-01
Thank you! :-)

---

### Post by lovinglinux on 2010-11-01
> **onaridge said:**
> Thank you! :-)

You are welcome.

---

### Post by nealegray on 2010-11-05
excellent, Ive been messing about for over an hour trying to get iplayer working, thanks.

---

### Post by JosephC on 2010-11-06
Another strange new phenomenon (beginning with Maverick) I encountered on 64-bit systems was that when I attempted to install Flash Square on a freshly installed 10.10 by, as usual, moving the .so to /usr/lib/firefox-addons/plugins, Flash didn't work. It was really puzzling, until I realized that the permissions of the .so were all set to "none." Evidently, moving the libflashplayer.so from an external disk changes the permissions, thereby rendering it useless to Firefox until you manually set all the permissions to "read only" by going to Properties>Permissions, etc.

---

