---
title: "trouble getting my wireless up and running!"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by camerong on 2007-01-14
hey all, thanks for reading this.

i cant get ubuntu to recognize my driver for my wireless dell 1450 usb adaptor. it does however, recognize the hardware itself. 

i have ndiswrapper installed and -utils too and the graphical interface for it, and i loaded my dell 1450 wireless usb adaptor's windows drivers onto it using the cd that came with it, and then i added the DELLNIC.inf file to ndiswrapper via the graphic interface and then checked its succes using the terminal, but it says:

> dellnic invalid driver!

this was the driver that came with my cd for my dell 1450 wireless usb adaptor. what do i do?

i have seached and used the wiki and asked on irc but still need help. thank you.

---

### Post by Metaljaz on 2007-01-14
Try this walkthrough for troubleshooting:

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

---

### Post by Metaljaz on 2007-01-14
Also you will need to know the chipset of the adapter.
Try running this command from the terminal window to find your
chipset:
lshw 

under network you should see product "name" and vendor "name"

post back

---

