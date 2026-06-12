---
title: "Radeon 9600 needs newer opengl drivers"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by nzfg on 2009-07-03
My graphics card is a radeon 9600 and the default drivers cant play warcraft 3 or savage 2.  i believe it may be version opengl 1.3 but i need something newer to run those and other games that i have.  does anyone know where or how i can fix it up so that this is possible.  much appreciated.


```
sam@sam:~$ glxinfo | grep "OpenGL version string"
OpenGL version string: 1.3 Mesa 7.4

```
```
sam@sam:~$ lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
```


New Zealand Fail Guy

---

### Post by caravel on 2009-07-03
You will need the fglrx driver installed to run that, but you have the open source ATI/Radeon driver installed.

What Linux distribution are you running?

---

### Post by nzfg on 2009-07-03
i'm using ubuntu 9.04.  the hardware drivers program in system admin doesnt give me any proprietary drivers available

---

### Post by caravel on 2009-07-03
> **nzfg said:**
> i'm using ubuntu 9.04.  the hardware drivers program in system admin doesnt give me any proprietary drivers available

This is because your card is now considered legacy and is not supported by the latest versions of the fglrx driver - including the one in the Ubuntu 9.04 repos.  Downloading older drivers won't help you either as the root cause of this is the upgrade of xorg in Ubuntu 9.04.

If playing this game is important to you, I advise you to format and reinstall Ubuntu 8.10 or 8.04.

---

