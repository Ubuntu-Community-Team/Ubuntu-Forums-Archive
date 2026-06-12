---
title: "I keep losing my Domain"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2008-04-26
I set up the domain by going to System->Administration->Network->General but when I reboot or restart the network I lose the Domain.

Is there a configuration file I can update so that it will be permanent?

---

### Post by High_Yield on 2008-05-04
I have the same problem.

Under "network", the domain name simply goes blank.
My domain is on a QNap TS-101 NAS running linux and I believe samba.

Please help - it's really annoying.

---

### Post by weaver4 on 2008-05-21
I found that I needed to edit /etc/samba/smb.conf and change the workgroup name to what you wanted and then reboot.  You will need to edit this file as superuser

sudo gedit /etc/samba/smb.conf

---

