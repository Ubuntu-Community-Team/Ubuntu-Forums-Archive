---
title: "Making NDISwrapper 'stick'"
date: 2005-10-04
forum: Networking &amp; Wireless
---

### Post by Starman on 2005-10-04
I have NDISwrapper installed and my Broadcom wireless card is functioning but I need to 'sudo modprobe ndiswrapper' everytime I restart. How can I make this happen automatically?

Thanks

---

### Post by skirkpatrick on 2005-10-04
Add the line "ndiswrapper" to /etc/modules.  You'll have to use sudo to edit the file.

---

### Post by az on 2005-10-04
...as in

sudo gedit

And then open the /etc/modules file.

---

