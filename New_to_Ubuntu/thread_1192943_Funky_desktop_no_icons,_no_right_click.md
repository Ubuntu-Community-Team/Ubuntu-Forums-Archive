---
title: "Funky desktop: no icons, no right click"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by m_ad on 2009-06-20
I noticed for a while now that I can't see anything that I download (or move) to my desktop. I have to go to Places->Desktop. After a little longer, I noticed I can't even right click my desktop either.. what's happened?

I'm running 8.04. Here's something that I thought might be useful to anyone who wants to help me.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

---

### Post by mike555 on 2009-06-21
Ubuntu tweak has a setting to show icons on desktop , you can get it here ;   [http://www.getdeb.net/category.php?id=10](http://www.getdeb.net/category.php?id=10)
  (make sure you get the one for the version of Ubuntu your using)

---

### Post by Arand on 2009-06-21
It might be that you've disabled the show desktop feature of the file browser (nautilus).

If this is the case you can re-enable it by starting "gconf-editor" (alt-F2 run dialogue, type "gconf-editor", run). Then you go to the "key" under /apps/nautilus/preferences/show_desktop, and make sure it is ticked.

- Arand

---

### Post by m_ad on 2009-06-21
> **mike555 said:**
> Ubuntu tweak has a setting to show icons on desktop , you can get it here ;   [http://www.getdeb.net/category.php?id=10](http://www.getdeb.net/category.php?id=10)
  (make sure you get the one for the version of Ubuntu your using)

cool, is this just a front end to the gconf-editor? this is helpful, but didn't solve the problem as it seemed my desktop was froze.

> **Arand said:**
> It might be that you've disabled the show desktop feature of the file browser (nautilus).

If this is the case you can re-enable it by starting "gconf-editor" (alt-F2 run dialogue, type "gconf-editor", run). Then you go to the "key" under /apps/nautilus/preferences/show_desktop, and make sure it is ticked.

- Arand

:D :D

I knew I did something in the gconf to try and get rid of the volume icons on the desktop. I couldn't remember, and apparently this was it. Fixed, thank you sir :D

---

