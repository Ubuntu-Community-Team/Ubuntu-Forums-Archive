---
title: "MSTT fonts not installing"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by zaivala on 2009-12-20
I've noticed that my browser is not showing Arial fonts,,, so I must not have installed msttcorefonts.

I went to my Terminal and typed:

sudo apt-get install msttcorefonts

and was greeted with:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
The following packages were automatically installed and are no longer required:
  python-crypto ttf-wqy-zenhei python-json libopenjpeg2 libdns50
  libempathy-common icon-slicer libtelepathy-farsight0 telepathy-haze
  libnspr4-dev telepathy-mission-control-5 libempathy-gtk-common
  telepathy-butterfly python-papyon
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So, nothing installed, and I'm being prompted to remove something which I fail to understand... maybe it's late or something.  Any ideas?

---

### Post by BenAshton24 on 2009-12-20
they're already installed...
> msttcorefonts is already the newest version.

you could at least have tried to read the output...

Also, run "sudo apt-get autoremove" coz u've got a load of stuff installed that you don't need...

---

### Post by zaivala on 2009-12-20
Short circuit between chair and keyboard.  My Arial font was not displaying on a website... because I didn't set it as the default font.  Damn, I hate it when I out-stupid myself.

---

