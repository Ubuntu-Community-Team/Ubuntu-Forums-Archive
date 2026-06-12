---
title: "Copy a USB install to another USB stick."
date: 2011-03-21
forum: New to Ubuntu
---

### Post by CVGH on 2011-03-21
I've got a usb-creator-gtk made install of 10.10 on a 16GB stick.
I'd like to copy this to another 16GB stick so I can give it to someone.
 Do I need to do this from the CLI using dd? Or can I do it in Gnome?

Thanks!!

---

### Post by andrewthomas on 2011-03-21
using dd seems to be the easiest way to me.

---

### Post by HermanAB on 2011-03-21
Howdy,

You could even use cat:
Plug in schtick
$ dmesg
Note device name, e.g. /dev/sdb
Do not automount it when something pops up.

Plug in other schtick
$ dmesg
Note device name, e.g. /dev/sdc
Do not automount it when something pops up.

$ sudo cat /dev/sdb > /dev/sdc

La voila!

---

### Post by C.S.Cameron on 2011-03-21
I've used dd with success:

dd if=/dev/sdb of=/dev/sdc

where sdb is what you want to clone and sdc is the target.

---

