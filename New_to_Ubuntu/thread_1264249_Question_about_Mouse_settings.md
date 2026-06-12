---
title: "Question about Mouse settings"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by linuxnoob53108 on 2009-09-12
I prefer to have different settings when I'm using my USB mouse VS. the touchpad on my laptop. I would like to write a quick script to change the settings so I would be able to click one shortcut to run a script after I plug in my USB mouse and click a different shortcut when I remove my usb mouse and use my touchpad, has anyone tried anything like this??

---

### Post by zephyrcat on 2009-09-12
I have never tried anything like that, but you might want to take a look at the xset command, which lets you change mouse (and other) X server configurations:

[http://www.manpagez.com/man/1/xset/](http://www.manpagez.com/man/1/xset/)
[http://linuxreviews.org/howtos/xfree/mouse_speed_in_x/](http://linuxreviews.org/howtos/xfree/mouse_speed_in_x/)

---

### Post by stderr on 2009-09-13
xbindkeys is what I use for configuring the buttons on my MX1000 - you may like to look into that.  You specify a config in ~/.xbindkeysrc, with instructions like:

```

"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[c]""
 b:8

```

where b:8 is referring to button 8 of my mouse, and when pressed, it executes xvkbd with arguments to simulate the pressing of Ctrl+C, or in other words, the copy shortcut. If you can discern the correct button numbers for your hardware, then you can create multiple ~/.xbindkeysrc files and easily swap them over with a bash script. You'd need to get xbindkeys to re-read then config, probably by killing it and restarting it. Something along the lines of 
```
kill -9 $(pidof xbindkeys)
xbindkeys&
```

Just speculating here, don't know if this will work in practice. Often you find issues where you thought there were none :popcorn: so it is with computing ;)

---

