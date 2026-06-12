---
title: "video drivers not installing"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by ave2 on 2009-11-01
In the terminal I used sudo + path to the display drivers- to install the latest ATI 4850 drivers for my card- I went through the wizard, and it eventually said process completed properly.
Now if I go into system/admin/hardware drivers 
it says
No Proprietary drivers are in use on this system...
ATI Proprietary FGLRX graphic driver is not activated, if I click activate, it wants to download new drivers... 

any idea what could be going on?

---

### Post by 3rdalbum on 2009-11-01
The Hardware Drivers program will only manage the drivers from the repository, not ones that you install manually.

It really is reccommended to stick with the repository drivers as they stay in sync with new kernel updates; manually-installed drivers will need to be reinstalled after every kernel upgrade.

---

