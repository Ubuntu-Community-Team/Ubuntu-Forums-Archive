---
title: "windows &amp; samba"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by jazzman8866 on 2008-01-23
i'm having trouble with windows xp and samba. my ubuntu system can see the windows shares, but windows can not see my ubuntu system. the closest i get is when windows asks me what my username and password is. i enter it, but to no avail. i just keep getting asked what my username and password s...no matter how many times i enter it.

any help or ideas would be appreciated. thanks heaps.

:confused:JAMES.:confused:

---

### Post by b0rka7a on 2008-01-23
**Please, search the forum before creating new threads!**

-HOWTO: Setup Samba peer-to-peer with Windows
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by swerdna on 2008-01-23
> **jazzman8866 said:**
> i'm having trouble with windows xp and samba. my ubuntu system can see the windows shares, but windows can not see my ubuntu system. the closest i get is when windows asks me what my username and password is. i enter it, but to no avail. i just keep getting asked what my username and password s...no matter how many times i enter it.

any help or ideas would be appreciated. thanks heaps.

:confused:JAMES.:confused:
The short answer is that you need to add a user to the samba user database. Then when windows asks for credentials, give the username (and password) that you added on the Linux machine. See the tutorial referenced above and zero into the smbpasswd stuff

Swerdna

---

