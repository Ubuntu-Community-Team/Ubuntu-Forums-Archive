---
title: "No Dial Up -  3Com 56k Robotics PCI Modem"
date: 2004-11-01
forum: Networking &amp; Wireless
---

### Post by jodef on 2004-11-01
The Modem is 3 COM V90 56k Internal/Voice Fax Modem Model 0727 
 Chipset 3CP3298-DEL 
 FCC ID 4X2USA-32034-M5-E ie a confirmed hardware modem.

Not very familiar with Gnome usually  kppp is my dial up tool of choice. Windows detects modem on COM5 ie ttyS4. Found the networking wizard tool and filled in necessary details, here are the steps normally required to get my modem working in most distros :Suse, Mandrake, Yoper, Slackware etc. 
```
cd /dev 
 mknod ttyS4 c 4 6 
ln -s ttyS4 modem
``` 
The properties tab of ppp0 shows the modem as /dev/modem but I am unable to connect. The autodetect option didn't yield any better results. Changing /dev/modem to /dev/ttyS4 no change.

Any ideas on how to troubleshoot the problem?

---

