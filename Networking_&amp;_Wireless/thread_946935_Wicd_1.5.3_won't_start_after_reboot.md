---
title: "Wicd 1.5.3 won't start after reboot"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Draghun on 2008-10-13
After having an older version Wicd decide to stop working for me, I upgraded to Wicd 1.5.3.  It found my WPA2 network and connected with no issues.  I restarted my laptop and I can't get Wicd to run again when I click either the shortcut I made or the entry under the Application menu.  Any ideas??

I'm on Gutsy and have a Broadcomm wireless card if it makes a difference.

edit:  The Command for my shortcut is wicd-client

---

### Post by imdano on 2008-10-13
Do you get any errors when you run ```
sudo wicd -foe
```

---

### Post by johanhartman on 2008-10-14
have you tried alt+F2 and then entering "wicd --replace"?

---

