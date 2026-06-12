---
title: "Uninstalling Amarok"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by KeremE on 2011-06-03
Hi, I just dowloaded Ubuntu, and after trying out Amarok, tried to uninstall it with the command "sudo apt-get remove amarok" in terminal. However, its icon still shows up when I click on the volume button on the taskbar. How do I uninstall Amarok completely?

---

### Post by Anuovis on 2011-06-03
Try this, might help:
*sudo apt-get purge amarok*

---

### Post by rosencrantz on 2011-06-03
The Amarok icon shows up when you click on the volume button? That one belongs to the Kmix tray app and shouldn't have anything to do with Amarok.
An easy way to find put whether Amarok is still on the system would be typing 'which amarok' in the terminal - if it doesn't return 
anything, you succeeded in uninstalling.

Did you restart/log out since uninstalling?

---

### Post by KeremE on 2011-06-03
Rebooting did the trick. Thanks for the help!

---

