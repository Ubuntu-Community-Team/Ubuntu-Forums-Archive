---
title: "Could not move the cursor in Grub menu"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by pcpain on 2009-08-05
I just re-installed Ubuntu 9.0.4. to the PC to co-exist with Windows XP. Now I could not move the cursor in the Grub menu either with the mouse or the arrow keys. The high-lighted selection is the first menu selection,  and it is activated after the time-out but cannot be activated by pressing the enter key. It appears that the key board is locked up.

I examined the menu.lst and changed the default selection. Nothing is unusual and the default selection could be changed.

Any suggestions? I prefer not to re-install the 9.0.4.

---

### Post by tjwoosta on 2009-08-05
maybe this might help?

[http://ubuntuforums.org/showthread.php?t=1081791](http://ubuntuforums.org/showthread.php?t=1081791)

---

### Post by pcpain on 2009-08-05
After some tinkering, I modified the xorg.conf file by defining the keyboard more completely (such as Option "CoreKeyboard", Option "XkbRule" "Xorg", Option "XkbModel" "pc104" and Option "Xkblayout" "us"). The problem just disappeared. This has to be my lucky day!

---

