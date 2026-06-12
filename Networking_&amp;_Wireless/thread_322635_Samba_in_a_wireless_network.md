---
title: "Samba in a wireless network"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by giancarlo76 on 2006-12-20
I tried Googling a lot, but I didn't find anything that can help me. Simply, I can't share my Linux folders through the smb protocol anymore in my wireless network. No problem with cabled network. I tried several different tutorials, with no success. Any hint?

---

### Post by dbbolton on 2006-12-20
could you show your samba.conf file ?

---

### Post by kylevan on 2006-12-20
yeah, it's possible that samba is not set up to allow shares over your wireless interface.

If you go to this tutorial: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) and scoll down to section 3, "security consideration" you'll find info on that.

---

### Post by giancarlo76 on 2006-12-21
> **kylevan said:**
> yeah, it's possible that samba is not set up to allow shares over your wireless interface.

If you go to this tutorial: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) and scoll down to section 3, "security consideration" you'll find info on that.

I followed that tutorial and now everything works. Maybe I only needed to map specific interfaces.
Thanks a lot!

---

