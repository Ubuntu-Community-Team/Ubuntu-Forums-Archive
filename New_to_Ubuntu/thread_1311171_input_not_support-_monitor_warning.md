---
title: "input not support- monitor warning"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by ave2 on 2009-11-02
Iv got a problem with my stupid acer monitor, It was doing the same thing in 8.10... here is the problem

when I first booted up ubuntu, everything looked perfect on the screen but I had a large blue block right in the center saying "input not support" it never goes away, but just stayed there there whole time, until I changed the resolution from 1680 x 1050 (16:10)  to  1280 x 960 (4:3) then the block disappeared. so I guess its got something to do with default resolution

now the problem im having is that if I log out, the log on screen has this blue block on it and covers all the log in options, so in other words the only way I can use ubuntu is as the default user, with auto login, I cannot have more than one user

is there a way to change the resolution of the log on screen (it does the same during the entire installation, and on the ubuntu splash screen when I start up each time) has anyone else had this problem, is there any way to solve this
I have the Acer Ferrari 19"

---

### Post by ave2 on 2009-11-02
I finally solved it by following the following suggestions:

[http://ubuntuforums.org/showthread.php?t=151192](http://ubuntuforums.org/showthread.php?t=151192)
[http://ubuntuforums.org/showthread.php?t=359310](http://ubuntuforums.org/showthread.php?t=359310)

quoting the following:

```
cp /etc/X11/xorg.conf /home/<Your Username>/Desktop
```

```
gksudo gedit /etc/X11/xorg.conf
```


changed this (in my xorg.conf file):

```
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

to this:
```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		[COLOR="Red"]Modes    "1152x864" "1024x768" "800x600"[/COLOR]
	EndSubSection
EndSection
```

---

