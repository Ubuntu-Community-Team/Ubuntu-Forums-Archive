---
title: "Samba Issues"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by WALZ on 2008-09-01
[FONT="Lucida Sans Unicode"]Hello all.  I've had Samba set up and running (thanks to [Stormbringer's great guide](http://ubuntuforums.org/showthread.php?t=202605)) for a few weeks now, but all of a sudden my Windows computer is refusing to connect.  I get "The mapped network drive could not be created because of the following error has occurred: An extended error has occurred."

No settings have changed.  The issue started after my Windows machine froze and I had to do a hard reboot.  I've tried restarting Samba, restarting both machines, checking the config files, and resetting the passwords with no success.  I'm pretty sure something is messed up on the Windows side.  Anyone have any thoughts of what I can try next?

Thanks,
WALZ[/FONT]

---

### Post by modmadmike on 2008-09-01
Samba can get messed up if another computer thinks its the "Master" however this usually only occurs when you have another networked linux box (and this even includes Store bought Network storage devices based of unix/linux) I have had many problems with samba, but usually in viewing widows computers not the other way around. 

When i searched google i got 239000 results so this is a common WINDOWS problem not samba, your best checking windows forums not linux :(.

---

### Post by prshah on 2008-09-01
> **WALZ said:**
>  but all of a sudden my Windows computer is refusing to connect.  I get "The mapped network drive could not be created because of the following error has occurred: An extended error has occurred."


Apparently one cause for this is a time issue; the time on your ubuntu and XP box should be within 5 minutes of each other. Can you check this? 

If you would like to synchronize the time, in XP you can use the command```
net time \\ubuntubox /set
```

(Replace ubuntubox with the actual name/ip address of your ubuntu box.)

---

### Post by WALZ on 2008-09-01
[FONT="Lucida Sans Unicode"]I just double checked and both are within seconds of each other.  I have them both set to auto adjust to the same time server.[/FONT]

---

### Post by prshah on 2008-09-01
> **WALZ said:**
>  both are within seconds of each other.  I have them both set to auto adjust to the same time server.

OK, Step 2: Is the "Routing and Remote Access" service required/activated? Click Start-Run-"services.msc" and then check the above service: If it is not started, start it and then try to connect. 

If it connects fine, you can change the startup from "Manual" to "Automatic". Otherwise, you can just stop this service, to prevent unnecessary changes to your configuration.

---

### Post by WALZ on 2008-09-01
[FONT="Lucida Sans Unicode"]That service was disabled (I've had it disabled for a long time) but turning it back on had no change on the situation.

***EDIT: Figured it out.  Was something silly on my part with the Ubuntu machine.  My bad.***[/FONT]

---

### Post by waynemeister on 2008-09-19
Hi walz what was your silly mistake?

---

