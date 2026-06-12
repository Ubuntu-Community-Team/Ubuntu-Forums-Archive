---
title: "can`t silence modem while dialing"
date: 2005-07-05
forum: Networking &amp; Wireless
---

### Post by jimjim on 2005-07-05
i have tried using m0 between at and dt in sudo gedit /etc/chatscripts/provider with no luck in keeping the modem noise quite.  does anyone know why this may be happening and how can i remedy this?   thanks in advance. jim   the modem i use is a hayes external serial port.  i have solved this problem.  i went to /etc/chatscripts/ppp0 and added m0 between at and dt. my first post indicated the wrong chatscript.

---

