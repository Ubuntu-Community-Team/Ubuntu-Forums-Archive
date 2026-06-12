---
title: "Bind stops after hostadd dns"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by titan1000 on 2007-09-21
added a few entries to dns and bind stopped. 

ps -ef | grep named spawned off many processes.  kept changing the number of processes.

finally pkill and started named.

IS there any best practices which mentions that dns updates (to the host table i.e.) should only be done off hours?

---

