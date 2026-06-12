---
title: "Then network-manager applet didn't show in the ubuntu utopic?"
date: 2015-04-11
forum: Networking &amp; Wireless
---

### Post by shamsat on 2015-04-11
The network-manager applet was there but after installing some packages now the network-manager applet didn't show, when i click to open the network icon from the dash board cannot work and get the error:
> 
The system network services are not compatible with this version 

i run the commands "apt-get update" then "aptitude full-upgrade" and "aptitude install -f " get this output:
> 
# aptitude full-upgrade
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

This is the nmcli command output:
> 
# nmcli nm
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
not running     unknown         unknown         unknown    unknown         unknown 


---

### Post by bapoumba on 2015-04-11
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1127151](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1127151)
May be this ?

---

