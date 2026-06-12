---
title: "Need one keybind to work. Logitech G5"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by Melhisedek on 2009-07-04
Hello there, I just installed Ubuntu and most of the stuff work out of the box. I have Logitech G5 mouse and I need left horisontal scroll as a middle mouse button. Middle mouse can be pressed and tilted left and right, sadly mouse is pretty old and when i try to press middle button sometimes it register as left or right tilt so thats why I bind it just to left tilt to be sure it works. 

All the buttons on the mouse work although there is no entry for mouse in my xorg.conf
```

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection
```

In any case how do I make my left tilt act as a middle mouse press?

Thank you for your time!

---

### Post by Melhisedek on 2009-07-05
Bump

---

### Post by CatKiller on 2009-07-05
Input devices aren't handled by xorg.conf now, they're handled by HAL, so that they can be hotplugged. You might find some information in [this thread]("http://ubuntuforums.org/showthread.php?t=948154").

---

### Post by Melhisedek on 2009-07-05
I'm trying to follow this thread:

[http://ubuntuforums.org/showthread.php?t=968530&highlight=logitech+g5+xbindkeysrc](http://ubuntuforums.org/showthread.php?t=968530&highlight=logitech+g5+xbindkeysrc)

and am trying with this code in /.xbindkeysrc:

# Mapping middle click to tilt left
"echo 'ButtonPress b:2 ButtonRelease b:2' | xmacroplay :0"
b:6

But it just wont work, I think it repeats some strange press as I lose control over mouse and can only use Keyboard after I tilt left.

Any ideas?

---

