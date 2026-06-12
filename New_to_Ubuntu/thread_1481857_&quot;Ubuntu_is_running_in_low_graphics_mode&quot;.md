---
title: "&quot;Ubuntu is running in low graphics mode&quot;"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by nel05 on 2010-05-13
[B]create first a back up of /etc/X11/xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bckp

then Edit  /etc/X11/xorg.conf

-Add this entry below to the Device section

Driver       "vesa"


'reboot the system'
-its a generic graphics card driver
-no more promt of Ubuntu running in low graphics mode--:)

[/B]

---

