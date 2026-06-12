---
title: "Atheros wireless stopped working after updates"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by gapalp on 2005-04-11
I have been running the Hoary preview for a couple of months now on a Thinkpad X31. The Atheros wireless has worked fine with no problems until a couple of days ago. After installing a set of updates and a reboot, the wireless adapter no longer shows up as a device.
I have not tried reinstalling Hoary or using ndiswrapper. That may work but I would rather know why it stopped and what to do to fix it so Hoary sees the wireless as it did before. Seeing as I get the updates as they come out, if I reinstall Hoary and it works, whats to say when I do another update it will stop working again?
Any help or suggestions would be appreciated.

---

### Post by alastair on 2005-04-11
I don't know but .... if you are using NDISwrapper, what happens when you try and load the driver? I believe there are verbose or debug options on load/probe. Messages?

Anything printed in the log file /var/log/syslog?

---

