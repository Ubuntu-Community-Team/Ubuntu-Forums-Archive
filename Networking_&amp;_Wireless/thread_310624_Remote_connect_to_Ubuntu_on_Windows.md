---
title: "Remote connect to Ubuntu on Windows"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by Eddy Dean on 2006-12-01
Hello,

I would like to know if it's possible to remote connect into an Ubuntu machine from Windows. This has to be done with no client applications. It is so I can use my own machine at school, but I'm not allowed to install any applications in school.
I know Windows has a remote desktop feature, but I'm not sure if that works for Linux remote desktops. I know how to configure a linux remote desktop, but that has to do with vnc-thingies.


Thanks in advance,
Eddy Dean

---

### Post by anorexicpillow on 2006-12-01
uhhh this possibly [http://doc.gwos.org/index.php/DapperGuide#How_to_configure_remote_desktop_.28not_secure.29](http://doc.gwos.org/index.php/DapperGuide#How_to_configure_remote_desktop_.28not_secure.29)

---

### Post by technodigifreak on 2006-12-01
> **anorexicpillow said:**
> uhhh this possibly [http://doc.gwos.org/index.php/DapperGuide#How_to_configure_remote_desktop_.28not_secure.29](http://doc.gwos.org/index.php/DapperGuide#How_to_configure_remote_desktop_.28not_secure.29)

that requires vncviewer on the windows (client) machine.

TightVNC (and probably RealVNC/UltraVNC) viewer only application does not require installation and can be run directly from the single executable.  [http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

If you only need a command-line secure connection then you can use Putty(SSH).  It's single exe that doesn't need to be installed so you can carry it on your flash-drive or a business card sized cd-rom in your wallet.  [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

:D

---

### Post by Slim Odds on 2006-12-01
> **Eddy Dean said:**
> This has to be done with no client applications.

This was to be done with no software.   :-D

That's harder then you think. :mrgreen:

---

### Post by Eddy Dean on 2006-12-03
So windows has nothing of use installed by default? Too bad. I'll see what I can do by just booting from an live CD, but I'm not sure if that's allowed at school...


Thanks anyway,
Eddy

---

### Post by brandon079 on 2007-09-29
Does VNC for ubuntu have a web client access like it does for windows?

---

