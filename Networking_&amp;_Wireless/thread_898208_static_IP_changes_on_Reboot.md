---
title: "static IP changes on Reboot"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by brijith on 2008-08-23
Hai All,

In my Office we are using **Debian Etch**. We are having a strange issue in our two newly Installed PC. In both systems we set static IP. But on restart ,some times on the run,  it changes to some other IP. The network interface goes on increasing (eth0, eth1, ...). Why This Happens. If any have a solution to this please share it.


[COLOR="Red"]**Thanks**[/COLOR]

---

### Post by spd106 on 2008-08-23
Hello,

You probably want to check the udev rules are configured correctly. See this page for information [http://www.debianhelp.co.uk/udev.htm](http://www.debianhelp.co.uk/udev.htm)

You'll want to look at the following rule before you make any changes
 /etc/udev/rules.d/70-persistent-net.rules

---

