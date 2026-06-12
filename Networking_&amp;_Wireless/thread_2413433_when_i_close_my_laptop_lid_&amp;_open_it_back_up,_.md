---
title: "when i close my laptop lid &amp; open it back up, my wifi will not connect"
date: 2019-02-25
forum: Networking &amp; Wireless
---

### Post by rebellious.ben on 2019-02-25
I have peered through a couple threads & tried out some things but nothing has worked.  My laptop is about a month old now, it's a HP - When I first installed Ubuntu 18.04.1 on it my WiFi was completely not found and i had to install rtl8821ce.  Once i did that my laptop picked up the WiFi.  But its a minor inconvenience.  When i close my lid & open it, I have to restart my laptop for my WiFi to work.  If anyone has any ideas please help, thanks.

---

### Post by TheFu on 2019-02-25
Look for power-standby threads - "ubuntu sleep rtl8821ce" would be a query..  Shutting the lid should disable the device and opening it should re-enable it, while starting up networking.  I had to manually configure it years ago for my intel wifi chips, but that hasn't been necessary since.

Look at /var/log/pm-powersave.log for some more ideas.

I think config files are in /etc/pm/

BTW, did you try this; [https://ubuntuforums.org/showthread.php?t=2004690](https://ubuntuforums.org/showthread.php?t=2004690) - you'll need to tweak it for your specific wifi driver.
and [https://askubuntu.com/questions/1102424/rtl8821ce-wifi-driver-cant-connect-after-suspend-or-change-network-on-ubuntu](https://askubuntu.com/questions/1102424/rtl8821ce-wifi-driver-cant-connect-after-suspend-or-change-network-on-ubuntu) seems to have a longer, more complex, solution.

---

### Post by rebellious.ben on 2019-02-26
It won't let me save the config file on the first link that you have gave, do you know how I could fix that problem?

---

### Post by TheFu on 2019-02-26
> **rebellious.ben said:**
> It won't let me save the config file on the first link that you have gave, do you know how I could fix that problem?

All Unix-like systems are multi-user.  A good understanding of that and file permissions is necessary.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)  File permissions are the cornerstone for all Unix security and this applies to every Unix system, which is basically every computer you use, unless it runs the single popular OS which is not based on multi-user Unix.  Every other computer you have **is** based on Unix.

tl;dr

use **sudoedit /path/to/file**
But only use it when necessary and proper. Using it at other times can cause many issues.

---

