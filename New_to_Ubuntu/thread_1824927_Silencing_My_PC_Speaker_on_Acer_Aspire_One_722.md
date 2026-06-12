---
title: "Silencing My PC Speaker on Acer Aspire One 722"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Ca648 on 2011-08-14
Hello! 

I have been searching the web trying to figure out how to silence my obnoxious pc speaker. I have found some really simple solutions about blacklisting that look like this:

$ sudo rmmod pcspkr
and
/etc/modprobe.d/blacklist then adding blacklist pcspkr

but those solutions wont work for my Acer Aspire One 722. This computer beeps loudly enough to break windows whenever I plug and unplug my computer. I want to eliminate this sound so that when I am in a library or some public place I do not disturb other folks. Your help would be greatly appreciated. Thanks!

---

### Post by LowSky on 2011-08-15
check the computer's bios.

---

### Post by Rubykuby on 2011-11-13
Old topic, but found the solution here:

[http://housegeekatheart.blogspot.com/2011/10/disable-ac-adaptor-beep-in-portables-in.html](http://housegeekatheart.blogspot.com/2011/10/disable-ac-adaptor-beep-in-portables-in.html)

In terminal:
[FONT="Courier New"]alsamixer[/FONT]
Then press F6.
Select the sound card that shows a "beep option".
Use arrow keys to navigate to the beep option, then use the down arrow to make it zero. If you're really paranoid, use "m" to mute it, too.
Press escape to quit.

When you plug in/out now, the beep will not be gone, but it won't slightly disturb anyone in the sense that it's really soft now.

---

