---
title: "ubuntu 7.10, dell latitude d620, bcom connects, but no response from websites"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by niiiick on 2007-12-23
hey guys; so i got the bcom stuff installed by downloading the deb for bcomxxx-fwcutter (or something like that) and then going to system->administration->restricted drivers manager and clicking enable next to the broadcom stuff.

it now shows wireless networks that are available and even allows me to connect to them.

it SAYS connected, but i am unable to access websites through firefox, unable to ping websites from the terminal, and even unable to access my router website.

any ideas?

---

### Post by csat on 2007-12-23
Well, I'd suggest you to install wicd as your network manager.  Check it from [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)  and observe download instructions for Ubuntu.

If you still have the same problem you can also check this thread:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

My Dell 131 L with the same broadcom wireless board is working fine.

---

### Post by bigken on 2007-12-23
open firefox in the browser type about:config in the search filter type ipv6 change its value from true to false by double clicking on it

---

### Post by niiiick on 2007-12-23
^^^tried that; no avail.

tried blacklisting ipv6, no avail.


perhaps i'll try wicd...do i need to uninstall network-manager?

EDIT: after installation of wicd (and automatically uninstallation of nm) i can connect to the wired network, but cannot obtain an IP address from the wireless.  the wireless is using WEP security.

---

