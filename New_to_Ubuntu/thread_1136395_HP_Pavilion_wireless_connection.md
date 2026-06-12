---
title: "HP Pavilion wireless connection"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by etgohome on 2009-04-25
[SIZE=2][COLOR=black]**I have just done first install into HP Pavilion ze4800 with Ubunutu 7.1 .   Cannot get a wireless connection.  When try, it just opens up a greyed out page for connection types.  Anyone got any ideas, like maybe theres a compatible driver somewhere.  HP no help at all.:confused:**[/COLOR][/SIZE]

---

### Post by anewguy on 2009-04-25
First we'll have you post back the output from the following, then we'll try to go from there:

Both in a terminal window - if you have never opened a terminal window before, it can be found under applications/accessories/terminal.  Sign in with your normal userid and password.

type:

sudo lspci <press enter>

sudo lsusb <press enter>

Post the results of those (you should be able to copy and paste) back here and we'll try to go from there.

Dave :)

---

### Post by Peter09 on 2009-04-25
Can you confirm the version of Ubuntu that you are using 7.1 or 9 (Jaunty)

---

### Post by RyanVanDiemen on 2009-04-25
> **etgohome said:**
> [SIZE=2][COLOR=black]**I have just done first install into HP Pavilion ze4800 with Ubunutu 7.1 .   **[/COLOR][/SIZE]

if it`s really 7.10 version you installed, you`d better download the latest version (9.04) because each new kernel has support for new  hardware. It might work straight after the install. New ubuntu shouldn`t be slow for this laptop. Even if it is you can still install new xubuntu 9.04 - it`s really good.

---

