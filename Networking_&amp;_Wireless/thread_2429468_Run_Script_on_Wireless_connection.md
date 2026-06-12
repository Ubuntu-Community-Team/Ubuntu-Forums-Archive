---
title: "Run Script on Wireless connection"
date: 2019-10-18
forum: Networking &amp; Wireless
---

### Post by imraan21 on 2019-10-18
I have installed Lubuntu 18.1

I have a simple script to VNC into another PC.

```

#!/bin/bash

xtightvncviewer 192.168.1.10:5

```

I would like to only trigger this script when a successful wireless connection is made.

I created this script in my home folder and then moved this script into /NetworkManager/dispatcher.d using [COLOR=#242729][FONT=Consolas] sudo mv -f -i[/FONT][/COLOR]
I then made it executable using [COLOR=#242729][FONT=Consolas]chmod +x.

[/FONT][/COLOR]My script is unfortunately not executing on boot up and successful connection.

Under /network/interfaces it states:  #ifupdown has been replaced by netplan(5) on this system. See /etc/netplan for current configuration.
Under /netplan/network-manager.yaml it states:  #Let NetworkManager manage all devices on this system.

I am unsure why my script is not running on successful network connection, and do not know how to troubleshoot this.
I know my script works because if I click it and execute it manually the VNC works.

Any ideas on where to look and fix this?
Thanks

---

### Post by slickymaster on 2019-10-18
Thread moved to **Networking & Wireless** for a better fit

---

### Post by imraan21 on 2019-10-18
> **slickymaster said:**
> Thread moved to **Networking & Wireless** for a better fit

Thanks man was not sure of the right place.

---

### Post by TheFu on 2019-10-21
18.10 support ended last July.  Please move to either 19.04 or 19.10, depending on your tolerance for bugs. 

BTW, 18.10 ---> 2018, October, so the ".10" is important and the zero should NOT be dropped.

VNC usually listens on port 5906, not "5".  All ports less than 1024 require the daemon be run as root, which is a huge security failure.  You've shown the client-side, but not the server-side.  I haven't used VNC in about a decade, generally use x2go at this point since it includes an ssh tunnel and basically always works if ssh is working between the 2 systems.  Also, x2go feels 2-3x faster than any VNC.

---

### Post by guiverc on 2019-10-21
I'll provide the following, related to bumping 18.10 to 19.04

1: Lubuntu manual reference on upgrading

[https://manual.lubuntu.me/stable/D/upgrading.html?highlight=release%20upgrade](https://manual.lubuntu.me/stable/D/upgrading.html?highlight=release%20upgrade)

2: Lubuntu 19.04 release notes

[https://lubuntu.me/disco-released/](https://lubuntu.me/disco-released/)

3: Backup always first, and if you have problems, I usually have prepared (mentally anyway; another box where I can download & write the 19.04 install media to a thumb-drive, and install using that if required. Use the 'manual partitioning' option and select my existing partitions but ensure I don't have format box checked. It will take note of additional packages you've added, wipe system directories, install, re-add back additional packages without touching your user files unless you had format selected. You should still have backups of any files you don't want to lose.  User configs saved in your $HOME won't be touched, however any configs saved in system directories will be lost because it wiped system directories (not an issue for most end-user applications).

Provided just in case useful, and askubu thread was deleted.

---

