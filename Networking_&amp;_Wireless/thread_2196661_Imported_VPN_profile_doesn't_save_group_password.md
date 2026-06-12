---
title: "Imported VPN profile doesn't save group password"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by yakudzam on 2013-12-30
Hello! I have a *.pcf file with credentials for connect to Cisco VPN. 

Importing was successful, but when I want to connect - pop-up window requires group password. 

I'm checking that password - it's on place and saved. 
I've found the bug on this issue: [https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/883037](https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/883037), but still can't find the solution. Please help

---

### Post by eugen_nicoara on 2014-02-12
Hi,
Are you able to connect and use the vpn after you enter the group password? I'm having issues importing the pcf into network manager and I'd like to know if it's worth spending more time on that or no.

Here is what i did:
- installed Gnome 3 on Ubuntu 13.10
- added vpnc support
```
sudo apt-get install vpnc network-manager-vpnc network-manager-vpnc-gnome
```
- copied pcf file from Windows box
- removed ^M characters from pcf file
```
dos2unix -n original.pcf clean.pcf
```
- opened Network, pushed the small + button on the bottom left corner, selected VPN in 'Add network Connection' window and then selected clean.pcf file in 'Add Network Connection' window. 

- got an error saying:
"Cannot import VPN connection
The file 'clean.pcf' could not be read or does not contain recognized VPN connection information

Error: unknown error."

Am I doing something wrong? I even tried importing the conf file created from the pcf file using pcf2vpnc but that did not help either.
Thank you!

---

### Post by vilem-kebrt on 2014-09-30
Have same problem here, in final i used [https://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](https://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode) to decode group pw and added it manualy

---

