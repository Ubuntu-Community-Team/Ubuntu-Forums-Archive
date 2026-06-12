---
title: "need help following directions for changing video settings"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by libihero on 2009-02-03
im trying to follow the directions on this link:
[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)
but i cant get it to work out right.
it says to
"[I]After which I added the following to the Device section under the driver

Code:

Section "Device"
	........
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option      "TexturedVideo" "off"
        .........
EndSection[/I]
"
on sudo gedit /etc/X11/xorg.conf

my sudo gedit /etc/X11/xorg.conf gives:

[B]Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
[/B]
so what should my final look like??

---

### Post by NT4usB on 2009-02-03
> **libihero said:**
> im trying to follow the directions on this link:
[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)
but i cant get it to work out right.
it says to
"[I]After which I added the following to the Device section under the driver

Code:

Section "Device"
	........
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option      "TexturedVideo" "off"
        .........
EndSection[/I]
"
on sudo gedit /etc/X11/xorg.conf

my sudo gedit /etc/X11/xorg.conf gives:

[B]Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
[/B]
so what should my final look like??```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option      "TexturedVideo" "off"
EndSection

```

---

