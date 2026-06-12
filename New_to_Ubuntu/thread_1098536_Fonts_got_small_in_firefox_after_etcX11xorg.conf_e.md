---
title: "Fonts got small in firefox after /etc/X11/xorg.conf edit"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by ni ni on 2009-03-17
Hi all!

my login window was way too large so that i couldn't see the box to enter my name.  i ran the command
```

sudo gedit /etc/X11/xorg.conf
```

I changed this ```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

to this ```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
SubSection "Display"
	Modes "1024x768"
	Virtual 1024 768
EndSubsection
EndSection
```

Now everything is working great but the fonts in firefox (e.g. in gmail and facebook) are too small and they look different.  they look squished (to be nontechnical).

Ihave played around with ajusting the font and so on in firefox of course.

Can anyone help???


thanks x x x x

---

### Post by t0p on 2009-03-17
Not being able to see your display, I suspect that your fonts have *not* "shrunk" - your display resolution has increased so more fits on the screen. 

If you want to reduce the resolution (make the font bigger) you can adjust it under System > Preferences > Screen Resolution (I think - I'm not on an ubuntu machine right now).

---

### Post by ni ni on 2009-03-17
Hello!

It's my fonts, not my resolution. The fonts and size of my panel,panel menus , my browser, and all the buttons etc on the browser are fine.

Everything is at the nice resolution I like, except for the fonts *inside* the browser, on the web pages.

---

