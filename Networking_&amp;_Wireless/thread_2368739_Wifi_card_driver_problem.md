---
title: "Wifi card driver problem"
date: 2017-08-14
forum: Networking &amp; Wireless
---

### Post by oluyenyuru on 2017-08-14
Hello everyone.
When i first install ubuntu my wifi card didn't work. So i searched and find this driver and it worked.
[https://community.linuxmint.com/tutorial/view/1796](https://community.linuxmint.com/tutorial/view/1796)

But whenever i update ubuntu it was stoping to work (only wifi) and i was reinstalling it again. 
This time reinstalling didint work. Also cable connection is gone too. So i tried to uninstall but i couldn't do it.
Can you help me?
Thx.

---

### Post by vocx on 2017-08-14
> **oluyenyuru said:**
> Hello everyone.
When i first install ubuntu my wifi card didn't work. So i searched and find this driver and it worked.
[https://community.linuxmint.com/tutorial/view/1796](https://community.linuxmint.com/tutorial/view/1796)

But whenever i update ubuntu it was stoping to work (only wifi) and i was reinstalling it again. 
This time reinstalling didint work. Also cable connection is gone too. So i tried to uninstall but i couldn't do it.
Can you help me?
Thx.
Open a terminal and type
```

uname -r

```

This will show the version of the Linux kernel that you are using. According to that link you posted, the driver is meant for the older kernels 3.x and 4.4.x. Currently the kernel is already going to the 4.8.x and 4.10.x versions, so maybe it won't work with your current system.

Also, please see the sticky thread in this forum. You need to run the wireless script to troubleshoot the problem better. [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by deadflowr on 2017-08-14
*Thread moved to **Networking & Wireless**.*

---

