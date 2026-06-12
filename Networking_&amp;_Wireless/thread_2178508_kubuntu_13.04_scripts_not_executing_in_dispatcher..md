---
title: "kubuntu 13.04 scripts not executing in dispatcher.d"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by gear64 on 2013-10-03
I'm trying to execute a script in '/etc/NetworkManager/dispatcher.d'.  At this point I don't care if it's up or down, I just want something to execute for any state change of my wireless connection.
The current script is 'test'.  It is owned by root root.  Permissions are 755.  The contents of script are:

#!/bin/bash
ls > scanning.txt


If I execute the script from terminal my directory listing is written to scanning.txt.  If I disable/enable my wireless card nothing happens.  If I reboot nothing happens.  Documentation seems to imply it's as simple as dropping a script in the folder.  Is there something else I'm missing?  I've also tried manually restarting the Network Manger serverice.

---

### Post by gear64 on 2013-10-03
Realized that I need to set PATH variable or use absolute paths to commands in script.

---

