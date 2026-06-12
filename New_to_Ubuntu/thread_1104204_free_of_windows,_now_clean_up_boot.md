---
title: "free of windows, now clean up boot"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by hollowtd on 2009-03-23
I just got windows off my machine. Does anyone know how to make it so that I can get the boot cleaned up so that when I turn on my computer ubuntu starts automatically? I think I use gedit but am unsure how to do it. thanks

---

### Post by Malalo on 2009-03-23
you can gedit your /boot/grub/menu.lst file, make sure to set the "default" to "0" (or whatever Kernel version you want to boot to, see the list on bottom of file), and the "timeout" to whatever (mine is 3)

also, you could rem (adding a # in front of the lines) all lines pertaining to Windows...

oh, remember to sudo your gedit

---

### Post by hollowtd on 2009-03-23
I got the Windows xp text gone with gedit. Now, how do I make it so that I don't have to select the ubuntu generic in 8 seconds or less with other choices. I mean, i'd like to turn on the machine and it boot right up into ubuntu without having to select anything. cheers way in advance

---

### Post by Bachstelze on 2009-03-23
Just set a very low timeout (like 2 seconds or so) and make the menu hidden. You have to edit the GRUB config file

```
gksudo gedit /boot/grub/menu.lst
```

then change the [font="monospace"]timeout[/font] value to 2 and uncomment the [font="monospace"]hiddenmenu[/font] line.

---

### Post by jelle_ on 2009-03-23
the easiest way is to install KGRUBEditor from add/remove programs. this program allows you to do advanced changes in grub.

you can also use gedit or another text editor. open /boot/grub/menu.lst as root and add the two following lines. i assume ubuntu is placed at the first place. 
default 0
timeout 0

---

### Post by Bakon Jarser on 2009-03-23
oops

---

### Post by hollowtd on 2009-03-23
Got it for 2 seconds but not sure how to get rid of the other choices or even if I should. Thanks again so much. You guys are the reason I kicked Windows in the rearend. Cheers

---

### Post by ddnev45 on 2009-03-23
Don't get rid of the other choices (with the possible exception of Windows); if something happens to the default kernel, you can boot one of the other options and try to repair your system.

---

### Post by hollowtd on 2009-03-23
I'll stick with that then and be happy. Thanks so much.

---

