---
title: "background image for grub"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by canonical on 2010-04-11
i have installed windows 7 and ubuntu on my comp. i have tried to add background image in grub 1.94 beta4 by editing 05_debian theme in grub.d folder but still i am not getting any background image in grub 1.97 . any solutions?

---

### Post by drs305 on 2010-04-11
If you would post the contents of the following line so we can ask some questions:
/etc/grub.d/05_debian_theme, approximately line 17, or wherever you have added your image information:

1. In the meantime, is the image in the correct folder?
2. Have you run "update-grub"?
3. Do you see the "Found debian image..." in the terminal as "update-grub" is run?
4. Are you using gfxterm and not console in /etc/default/grub? Still commented:  #GRUB_TERMINAL=console[/QUOTE]

---

