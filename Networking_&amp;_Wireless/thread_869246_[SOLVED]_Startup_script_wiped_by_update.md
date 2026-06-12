---
title: "[SOLVED] Startup script wiped by update?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2008-07-24
My HP dv 9428 Broadcom 43xx needed a startup script fix to find the wireless at startup. I used Wieman01's fix:
[http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

and now it doesn't start wireless connection at startup.

Do I need to execute the same fix again? Or use a different value than before?

>  HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.
Some users reported (including myself) that the network has to be restarted every time after startup... Apparently this is a bug.

Here is a workaround that helps restart the network during boot so that one does not have to do it manually after logging on to the system.

Create startup script:
Quote:
sudo gedit /etc/init.d/wireless-network.sh
Add this line & save file:
Quote:
/etc/init.d/networking restart
Change permission (executable):
Quote:
sudo chmod +x /etc/init.d/wireless-network.sh
Create symbolic link:
Quote:
sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/S40wireless-network
**[COLOR="Red"][SIZE="4"][Note: You may have to choose a boot sequence other than S40.][/SIZE][/COLOR]**

Restart...

---

