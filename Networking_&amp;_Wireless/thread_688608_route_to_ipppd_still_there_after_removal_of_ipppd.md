---
title: "route to ipppd still there after removal of ipppd"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by mveltre on 2008-02-05
hi!

I've got a problem with ipppd ... installed it and de-installed it (with dselect). But the default-route to the ipppd is still there after boot. I de-installed all packages with name the name 'ppp' in there,  but the route still comes up. 

Does anybody know how to disable it on boot? 

Thanks,
markus

---

### Post by mveltre on 2008-02-05
ok...

I moved the two files
/etc/isdn/device.ippp0 
/etc/isdn/ipppd.ippp0

to a backup-folder, after a reboot the interface and route doesn't come up again. 

Maybe it's an idea to auto-remove or disable these both files when de-installing ipppd ?


Thanks,
Markus
(solved issue)

---

