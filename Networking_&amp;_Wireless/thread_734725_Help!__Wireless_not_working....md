---
title: "Help!  Wireless not working..."
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by dobson1 on 2008-03-25
Help!  I am having trouble getting my wireless to work on my laptop...  When i go to the network connections and select the wireless, it appears to connect up.....but I have not been able to get it to display any web pages.  It just says unable to display, no matter what   site I try to go to...Any help would be much appreciated.

---

### Post by rsarvi on 2008-03-25
check whether the router is protected by WPA or WES algorithm. If so u need to configure the same password in ur WLAN to get connected

---

### Post by Eiríkr on 2008-03-25
If you also have a wired connection on the same machine, the problem might actually be the very Network Manager app that is supposed to help manage your connections.  Network Manager is known to have very limited functionality, and apparently causes all kinds of trouble if you have both wired and wireless on the same machine.  Many threads I've read here on the forum strongly recommend replacing Network Manager with WICD, which unfortunately is not included in the Ubuntu repositories, and must therefore be downloaded from [its Sourceforge page]("http://wicd.sourceforge.net/").

Cheers,

Eiríkr

---

