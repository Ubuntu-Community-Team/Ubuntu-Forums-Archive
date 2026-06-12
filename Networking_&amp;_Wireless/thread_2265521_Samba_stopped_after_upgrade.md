---
title: "Samba stopped after upgrade"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by decrepit on 2015-02-15
Have just installed 14.04 on my PC, it's been on my laptop for a while. I did have both of them connecting OK. "Windows network" showed both machines, but now "windows network" is blank on both machines. I've tried ```
service samba start
``` which came back with no errors, but didn't make any difference. The smb.conf file looks to be as I set it up.
Any clues where to go from here please?

---

### Post by decrepit on 2015-02-19
Up date, it seems smbd is broken, "stop" or "start" smbd returns "Unknown Instance". I've also just installed Gadmin-Samba, that has activate-deactivate buttons. Activate seems to work, but it says, "Status: Activated, inactive servers: smbd nmbd. When I hit the deactivate button, I get a popup saying "stopping samba (smbd) failed", and the Status message is unchanged.

---

### Post by decrepit on 2015-03-02
OK it's working now, somehow, the interfaces had got commented out. You've got to have local host in the system.

---

