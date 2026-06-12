---
title: "Feisty Server 7.04 Wireless connections"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by luckylarry on 2007-07-28
Hi,

I want to run Feisty server with a wireless connection on my laptop, my LAN connection runs fine and I can use wireless perfectly well in the desktop edition - but I want to run and use the server version AND wirelessly - basically for portable web dev stuff. 

I have an Intel PRO/Wireless 3945ABG adapter.

Is there anyway I can get this running in network manager or another utility? I understand that the drivers for the Intel wireless card are part of the linux-restricted-modules-2.6.20-16-server package which can't be installed and isn't available from a repo (unless anyone knows otherwise) leaving me to install the generic kernal version, which of course works without issue.

At the moment Server edition just won't detect the wireless card. Is there anything I can switch on or install?

I'm still a linux n00b so go easy ;)

cheers,

Pete.

---

### Post by noob12 on 2007-07-29
Don't know about the server edition here.  On Feisty desktop, a version of this driver is shipped but you may have to enable it  in the restricted drivers manager **(System  | Administration | Restricted Drivers Manager**).

You can check if you have the driver already

> 
find /lib/modules  -name "*3945*.ko"


---

### Post by luckylarry on 2007-08-04
yeh it works in desktop fine, but the restricted drivers module for the server edition doesn't exist :/

---

