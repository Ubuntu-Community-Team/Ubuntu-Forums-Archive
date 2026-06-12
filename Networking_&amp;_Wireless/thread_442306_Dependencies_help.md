---
title: "Dependencies help"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by cursebg on 2007-05-13
Can someone tell me what are the dependecies for netwok-manager-pptp on an entirely new Feisty Fawn?

---

### Post by aysiu on 2007-05-13
This should help you: ```
 sudo apt-get install network-manager-pptp
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ppp pptp-linux
Suggested packages:
  kernel-patch-mppe
The following NEW packages will be installed:
  **network-manager-pptp ppp pptp-linux**
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 452kB of archives.
After unpacking 1655kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
``` So should this:
[http://packages.ubuntu.com/feisty/net/network-manager-pptp](http://packages.ubuntu.com/feisty/net/network-manager-pptp)

---

