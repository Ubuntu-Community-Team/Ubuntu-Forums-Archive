---
title: "Auto Rdp start with ltsp"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by incin on 2007-03-26
hi
i was wondering if anyone got a good way of making the RDP autostart with LTSP in Ubuntu 6.10?
i am making a pxe boot enviroment that is gonna work up against Vmware computers with rdp enabled. i have a completely configured LTSP on Ubuntu 6.10, except for the RDP part.
any help would be fine.

---

### Post by dmonty on 2007-03-28
Try this display manager:

```

#!/bin/sh
# The IP address is of your Windows Terminal Server.
# The loop respawns the login screen.
# Author: Dean Montgomery

while [ true ]; do 
  xinit /usr/bin/rdesktop -f 192.168.0.1 -- :2
  sleep 5;
done

```

You may want to write a proper init script with start/stop/restart which will replace the current display manager (ldm).

See **man rdesktop** for more options.

---

