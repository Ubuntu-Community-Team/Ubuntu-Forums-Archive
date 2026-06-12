---
title: "dontzap --disable doesnt work"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by System Monitor on 2009-04-25
Yes i do have dontzap installed. I type sudo dontzap --disable and it does not show any output but control-alt-backspace still doesnt work????

---

### Post by Tim Sharitt on 2009-04-25
You can disable dontzap by adding this to your /etc/X11/xorg.conf:

```
Section "ServerFlags"
        Option          "DontZap" "false"
EndSection
```

You will need to restart X for the changes to take effect.

---

### Post by adult swim on 2009-04-25
i havent treid the dontzap program, but i added the dontzap section to my xorg.conf.  i had to log out and log back in for the ctrl+alt+backspace to work.  i imagine the program would work similarly

---

### Post by lovinglinux on 2009-04-25
It wasn't working until I saw your post and hit the damn keys just to make sure before replying.  I didn't wanted to log off :mrgreen: 

Try rebooting and see if it works then.

---

