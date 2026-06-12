---
title: "No ndiswrapper after reboot"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by wfriesen on 2007-11-12
I have installed the latest ndiswrapper following the instructions [here/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/") and it worked fine, until I rebooted.

I have ndiswrapper in /etc/modules, but doing "modprobe ndiswrapper" doesn't appear to do anything. What commands do I need to use to get going again, and how can I automate the process?

Thanks.

---

### Post by luisromangz on 2007-11-12
You can modprobe ndiswrapper inside your /etc/rc.local file, it will be run at boot.

---

