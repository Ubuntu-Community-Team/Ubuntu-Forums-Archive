---
title: "Bluetooth Mobile File Transfers"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by K3nto on 2007-08-20
Im having trouble setting up a bluetooth connection between my SCH-u510 and my Dell XPS M1210 (using feisty). Ive followed a tutorial on this site, but just cant seem to get it to connect. The issue im having presents itself in the last line of code in the following:

```
kent@kent-laptop:~$ sudo apt-get install bluez-utils
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
kent@kent-laptop:~$ sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services                                         [ OK ] 
kent@kent-laptop:~$ hcitool dev
Devices:
        hci0    00:16:41:91:6C:70
kent@kent-laptop:~$ hcitool scan
Scanning ...
        00:1B:98:58:EE:B4       Kent's Phone
kent@kent-laptop:~$ sudo hidd --connect 00:1B:98:58:EE:B4
Can't get device information: Success
kent@kent-laptop:~$ 
```

---

### Post by kidders on 2007-08-21
Hi there,

Your post is confusing. The title mentions file transfers, but judging from the rest of it, you want to use your phone as an input device. What kind of bluetooth connection are you interested in making?

---

