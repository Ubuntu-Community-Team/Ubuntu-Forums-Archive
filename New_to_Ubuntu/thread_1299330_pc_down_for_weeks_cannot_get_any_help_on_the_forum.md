---
title: "pc down for weeks cannot get any help on the forum"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by workshop1702 on 2009-10-23
hi my pc has been down for a long time looks like i will have to go back to windows as i dont seem to be able to get any help sorting the problem.
the problem i have is that my pc was working ok , then i changed the leads connecting my monitor to my pc from the normal 15pin d type connector to the older bnc type with seperate red green blue as the picture quality is better with these old leads. when i restarted it booted up ok but in low resolution.
the resolution is so low i cannot even use terminal i get an error message saying it need minimum number of lines to operate, pressumably i dont have enough maybe this is because the dpi was set different than normal, this was necessary for my widscreen sony FW900 monitor.
Please can someone help me get it going again i really am at a total loss as to how to repair it when i cannot get the xorg on terminal to display.Its really annoying me know i have spent hours getting nowhere and will be forced to go back to windows if someone wont help. the thought of going back to windows is really depressing me . I would be most grateful of any help

---

### Post by spiderbatdad on 2009-10-23
not really sure what to suggest but have you tried booting into safe graphics from the f6 menu at start up? Or boot into recovery and reconfigure xsever with the command ```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by diesch on 2009-10-23
Maybe [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) can help you.

---

