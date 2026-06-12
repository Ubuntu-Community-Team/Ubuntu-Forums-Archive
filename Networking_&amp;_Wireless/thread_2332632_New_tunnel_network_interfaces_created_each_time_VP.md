---
title: "New tunnel network interfaces created each time VPN is used"
date: 2016-08-02
forum: Networking &amp; Wireless
---

### Post by Obnt on 2016-08-02
Hello,


I am using Ubuntu Mate 14.04 and I connect to an OpenVPN server manually, using the command line (could not find a GUI application) and an .opvn configuration file.


I noticed that each time I reconnect to a VPN server this way, a new tunnel interface is created: first there is only tun0, next time I use VPN there are tun0 and tun1, and so on. Only after reboot those interfaces are gone.


Am I doing something wrong? Can I avoid the accumulation of those tun network interfaces? Can I get rid of them somehow without rebooting?


My knowledge of linux networking is less than minimal. Thanks in advance for any clarification and help.

---

