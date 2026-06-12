---
title: "Missing synaptics section in xorg.conf"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by ____ on 2009-05-29
I was trying to turn on SHMConfig so I could use the GSynaptics but there is no ```
Section "InputDevice"
``` section. Should I just add one?

---

### Post by Gen2ly on 2009-05-29
Yeah, you'll have to.  Look at 'man synaptics' and you can add the options directly or use gsynaptics for a gui friendly version.

Here's an example:

[http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Configuration](http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Configuration)

---

### Post by OffAxis on 2009-05-29
have a look here:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by ____ on 2009-05-29
i got it to work with this [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig") :D

---

