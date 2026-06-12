---
title: "typed &quot;sudo reboot&quot; in terminal, now wont display desktop"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by libihero on 2009-01-24
when trying to fix my video display, i was following the directions and i typed in "sudo reboot".  now when my computer starts, it just gives me "kinit trying to resume image *blah blah*" then it says "kinit cannot resume image, doing normal boot" and it asks me for login and password, and then it just acts like a terminal.  how can i get it back to normal??

---

### Post by jimmy the saint on 2009-01-24
It is far more likely that your booting problem is related to what you did while trying to fix your display.  can you post a link the instructions you followed so we can see what you were trying to do?

---

### Post by PocketDog on 2009-01-24
Weird, I just had almost exactly the same error. Log in with your username and password at the prompt you're at. I typed ```
startx
``` which did something complicated but I was still where I was. ```
gnome-panel
``` told me it wasn't installed. ```
sudo install ubuntu-desktop
``` fixed a lot of things, including desktop. You can then type ```
ubuntu-desktop
``` to run Gnome, if it isn't working already.

---

### Post by libihero on 2009-01-24
i followed these directions:
[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)
i got to
Section "Device"
	........
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option      "TexturedVideo" "off"
        .........
EndSection
but my device had other stuff already in it, so i just added this to the top.  
i then did reboot and it gave me that problem

---

### Post by jimmy the saint on 2009-01-24
If you backed up the file like the tutorial suggests, follow the advice on restoring that backup.  If you didn't, then issue this commnad:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by libihero on 2009-01-24
k i fixed it, but do u think u could tell me if im supposed to delete what was already in device and add the options, or place it over, or what i did wrong?

---

