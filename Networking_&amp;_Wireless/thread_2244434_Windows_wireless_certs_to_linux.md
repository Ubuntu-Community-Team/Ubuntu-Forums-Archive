---
title: "Windows wireless certs to linux"
date: 2014-09-16
forum: Networking &amp; Wireless
---

### Post by cpdondo on 2014-09-16
We have a windows-based wireless system that relies on certs and such. Specifically, it's WPA2-enterprise, TKIP encryption, using MS EAP (PEAP) authentication.

I have a dualboot laptop.  No problem with the windows side getting on the network (obviously) but I have not been able to find a HOWTO or figure out how to coax the certs out of Windows, and then how to set up Ubuntu using PEAP authentication.

Surely I can't be the only person to run into this.  Anyone know of a howto or a guide for doing this?

---

### Post by varunendra on 2014-09-20
Ca-Certs are usually not necessary, and I believe they are not OS dependent either. Some commonly used certificates are provided in the "/usr/share/ca-certificates/" directory. If you know which one you need, you can do the related settings in Network Manager as shown in the attached screenshot :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=256558&stc=1&d=1411223231[/IMG]

Not sure how to locate the certificate file in Windows. Maybe a quick search on the net can tell you about that.

---

