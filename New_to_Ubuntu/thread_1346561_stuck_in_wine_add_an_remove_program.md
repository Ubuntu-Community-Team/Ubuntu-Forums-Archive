---
title: "stuck in wine add an remove program"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by oiiyan on 2009-12-05
[FONT=Arial][SIZE=3]Hi,

i am new to Ubuntu, current i am using Ubuntu 9.10, I installed SPSS program under wine and i got stuck in the middle, so i have to force quit. i already using add and remove feature but what it says the installation was interupted need to run setup again. so i install it back but the same problem happened, now the SPSS program is stuck inside add and remove menu.

1. how do i remove it?
2.if not remove, will it effect to the system?

Thanks....[/SIZE][/FONT]

---

### Post by Paddy Landau on 2009-12-05
> **oiiyan said:**
> how do i remove it?
I'm not sure how to remove a program manually from Wine. Have a look in ~/.wine/drive_c.

> **oiiyan said:**
> if not remove, will it effect to the system?
Wine programs run only under Wine. So if you don't run it, it won't do anything to your system. You're safe.

For future, I strongly recommend that you install Wine programs using [PlayOnLinux]("http://www.playonlinux.com/"). It makes installing and uninstalling easy. Even if the installation bombs, as it did with you, PlayOnLinux will make it easy to remove the old installation.

---

