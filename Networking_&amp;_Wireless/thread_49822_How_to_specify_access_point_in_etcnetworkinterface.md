---
title: "How to specify access point in /etc/network/interfaces?"
date: 2005-07-17
forum: Networking &amp; Wireless
---

### Post by Aaron.42 on 2005-07-17
My wireless works fine once I tell it what access point to use via the iwconfig command.  How can I specify the access point in the /etc/network/interfaces file?  I've tried the following without any luck.

wireless_iwconfig=ap {mac address of ap}
wireless_ap  {mac address of ap}

Thanks!

---

### Post by Natja on 2005-07-18
Hi,

Try :

wireless-essid {AP name}


;)

---

### Post by Aaron.42 on 2005-07-18
I have the essid in the interfaces file but that doesn't seem to help.  I also tried putting quotes around the "ap {mac address}" part but that didn't help either.  The wireless works great once I tell it what acess point to use.  I just wish I didn't have to do that after it boots.

---

