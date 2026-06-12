---
title: "ATI card problem!"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-05-21
I couldn't enable visual effects on my ubutnu 9.10, also some problem Occurred due to incompatibility with ati card 
 this is my card type:

[PHP]mbg@mbg-desktop:~$ lspci | grep -i VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
mbg@mbg-desktop:~$ [/PHP]

glxinfo outpot:

[PHP]mbg@mbg-desktop:~$ glxinfo | grep direct
direct rendering: Yes
mbg@mbg-desktop:~$ [/PHP]

what's the problem?

---

### Post by -humanaut- on 2010-05-21
Have you installed the proper hardware drivers through jockey?

---

### Post by MBG1987 on 2010-05-21
No, i've just installed ubuntu on my machine, i don't know what's messing, and i thing the drivers were installed by the ubuntu cd, but still there's Problems

---

