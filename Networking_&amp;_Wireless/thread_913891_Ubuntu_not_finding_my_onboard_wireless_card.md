---
title: "Ubuntu not finding my onboard wireless card"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by Rufman on 2008-09-08
For some reason when I do lspci and lshw my onboard wireless card is not shown.


I have a macbook pro and I'm running ubuntu as a vmware virtual machine (could be the reason for my problem??)


Thanks for the help Stephane

---

### Post by Ayuthia on 2008-09-08
> **Rufman said:**
> For some reason when I do lspci and lshw my onboard wireless card is not shown.


I have a macbook pro and I'm running ubuntu as a vmware virtual machine (could be the reason for my problem??)


Thanks for the help Stephane

The virtual machine will emulate hardware devices so you will not be able to find your wireless that way.  There should be some way to configure vmware so that it will use your wireless connection but I have not used vmware in a while and I forgot where it is.  Sorry.

---

### Post by Rufman on 2008-09-08
I read that VMWare doesn't directly emulate the wireless card i.e. it appears as some AMD card and as etho1 connection, not wlan1. I have checked this on my own installation and receive the same result. Am I missing something??

Is this something that has been resolved with a newer VMWare version? I'm on the newest version.

---

