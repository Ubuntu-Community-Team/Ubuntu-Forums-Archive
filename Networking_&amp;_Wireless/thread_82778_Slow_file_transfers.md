---
title: "Slow file transfers"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by avc on 2005-10-27
I'm using a Xircom NIC (Cardbus, model CBEM56G-100). It's supposed to run at 100Mbps but it takes 3 times longer to download the same exact file as when I use a 10Mbps Xircom NIC! Under Windows 2000 on the same laptop, the 100Mbps card works at full speed. Is there something wrong with the xircom_tulip_cb driver?

---

### Post by rolfpal on 2005-11-14
the xircom_tulip_cb driver is deprecated, blacklist it.

the xircom_cb is supposed to work, but I am having a lot of trouble with it.  

See [http://www.ubuntuforums.org/showthread.php?p=491614#post491614]("http://www.ubuntuforums.org/showthread.php?p=491614#post491614")

Cheers,

Rolf

---

