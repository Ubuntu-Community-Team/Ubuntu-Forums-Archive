---
title: "Stop automatically connecting"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by tobinlam on 2008-10-02
I "borrowed" my neighbor's wifi while I was having issues with my own and I can't figure out how to stop it from connecting automatically.  To make matters even more annoying, my neighbor has secured their wifi, so I get a password window for the network every time I boot my computer.  How do I stop this?

---

### Post by jmbargar on 2008-10-02
I suppose you are using network-manager in order to connect your pc via wireless. The preferred networks list is in /home/user/.gconf/system/networking/wireless/networks/ so, all you have to do is delete the directory that you can find into this path and which name will be your neighbor essid.

---

### Post by Mark_in_Hollywood on 2008-10-02
I would look to the panel for the wifi icon. Mine is the signal strength and is in blue colored bars.

Right click on that "un-check" wireless networking. Reboot. That should take the OS to where you want it to be.

---

### Post by tobinlam on 2008-10-02
That's what I was looking for. Thanks.

---

