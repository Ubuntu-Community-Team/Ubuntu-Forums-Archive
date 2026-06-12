---
title: "1min delay on boot / config net devices"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by banditti on 2005-07-30
I have a laptop with wifi and ethernet.  On boot, it pauses for a good minute when it gets to configuring network devices ....

How do I get it to stop doing that?

---

### Post by Ptero-4 on 2005-07-30
[QUOTE=banditti]I have a laptop with wifi and ethernet.  On boot, it pauses for a good minute when it gets to configuring network devices ....

How do I get it to stop doing that?[/QUOTE]
 Disable the automatic network device detection. The system slows down because it is trying to get ip adresses for your nic and wifi card but it probably can't get them because you're far from your home lan.

---

### Post by banditti on 2005-08-01
How do I disable my automatic boot config?

---

### Post by BanskuZ on 2005-08-01
[http://www.ubuntuguide.org/#permanentlydisableenableboot-upservices](http://www.ubuntuguide.org/#permanentlydisableenableboot-upservices)

---

