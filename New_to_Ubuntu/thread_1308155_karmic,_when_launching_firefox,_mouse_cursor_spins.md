---
title: "karmic, when launching firefox, mouse cursor spins forever"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by occams_beard on 2009-10-31
Just upgraded to karmic. When I launch firefox the mouse cursor keeps spinning, even after firefox is up and running.

Very very annoying. Any fix for this?

---

### Post by phillw on 2009-10-31
> **occams_beard said:**
> Just upgraded to karmic. When I launch firefox the mouse cursor keeps spinning, even after firefox is up and running.

Very very annoying. Any fix for this?


Mine stops when i finally tell FF what site i want it to go to. Does yours continue to spin AFTER you've gotten your site in the browser window.

Phill.

---

### Post by occams_beard on 2009-10-31
Yes, it keeps spinning. It eventually stops after about 30s... I guess because the spinning cursor (launch feedback?) times out after so long. 

If I keep it on the web page within firefox it does not spin, but if I move it off the web page it's still spinning.

Just really annoying having a big round spinning mouse cursor while I'm trying to work...

---

### Post by jwooton on 2009-12-12
Yea, mine does the same thing.  I've installed Ubuntu on both my pc's at home and they both do this same quirky thing.  Just more fuel for me to keep using Chrome.  I suspect this is a very widespread bug, surprised it hasn't been patched yet.

---

### Post by gmjs on 2009-12-13
Yes--Karmic has been a very disappointing release for me (I can't adjust the volume of audio playback without it freezing).

He's the best 'fix' I can think of for that issue at the moment.  At the terminal:

```
$ **[B]gksudo gedit /usr/share/applications/firefox.desktop**[/B]
```

This opens the firefox.desktop file for editing in gedit (the 'code' if you like for the 'Firefox Shortcut').

**Delete** the last line:

```
StartupNotify=true
```

then save and close.  It stops the mouse cursor spinning at all for that shortcut.

Fingers crossed for 10.04 LTS being a good one!

Hope that helps,

Graham

---

