---
title: "sshd host"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by shortylonglegs on 2008-09-12
I had an open-ssh host running on my computer, but disabled it when I left for school.  I now want to run it again, but I can't figure out how to get it to run.  I had it so it would automatically run at startup, but I would be happy if I could just figure out how to manually start it.

---

### Post by HalPomeranz on 2008-09-12
Assuming you still have the ssh packages installed on the system, then "sudo update-rc.d ssh defaults" should make it so that the server starts automatically every time you reboot.  "sudo /etc/init.d/ssh start" should start the server manually ("sudo /etc/init.d/ssh stop" if you want to shut it down temporarily).

---

