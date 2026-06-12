---
title: "[SOLVED] System Beep Sound"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by akkad on 2009-01-01
since 8.10, whenever i restart or shutdown the system it raises a system beep, how possible to disable this sound?

i tried the settings in the system sounds and the power management but useless.

---

### Post by adult swim on 2009-01-01
from a terminal run ```
sudo rmmod pcspkr

gksudo gedit /etc/modprobe.d/blacklist
``` when the text editor pops up go to the end of the file and add a new line ```
blacklist pcspkr
``` then save and close the file.

---

### Post by akkad on 2009-01-01
heeeey this is too fast :D, as this huge community then i think it will be very soon when ubuntu will be installed over 70% of world wide Systems, 20% windows and 10% mac ;) ...
thnx anyway, let me try and restart my system.

---

### Post by akkad on 2009-01-01
solved, thnx bro.

---

