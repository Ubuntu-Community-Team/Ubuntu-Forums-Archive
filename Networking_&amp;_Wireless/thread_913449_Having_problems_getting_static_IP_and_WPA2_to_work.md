---
title: "Having problems getting static IP and WPA2 to work ?"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by ialexei on 2008-09-07
The system->networking application allows you to manually configure your network settings. If you disable roaming it will let you choose WE/WPA/WPA2/..

Problem is it will revert back to using WPA when you close the dialog. I did;nt have much luck after playing with /etc/network/interfaces.If you are in the same boat you can try the cool networking admin tool called wicd.

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

It worked like a charm. I hope the Xubuntu guys fix the broken admin tool or replace it with wicd.

---

