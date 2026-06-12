---
title: "WPA connection fails after suspend/resume"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by MikeRussell on 2008-04-24
Hi all,

    Running 8.04 on an Inspiron 1420 laptop here.  My wireless at home is WPA encrypted and I have no issues connecting to it..at first.  The problem occurs when I suspend and resume my computer.  I can occasionally reconnect, but more often than not I fail to make a connection.  I've had this problem using both gnome-network-manager and WICD.  I don't think it's driver related, because 'iwconfig' shows the network, but attempting to reissue a DHCP fails.  My best guess would be a conflict in issuing a new encyption key?  Any ideas on how to troubleshoot or fix this?  Thanks.

---

### Post by kevdog on 2008-04-25
Yes try connecting from the command line!
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by MikeRussell on 2008-04-25
Thanks for the quick reply.  I've tried 'sudo dhclient wlan0' and I hang when trying to acquire a DHCP lease.  It eventually times out an gives me a 'DHCP client sleeping error'.

---

### Post by kevdog on 2008-04-25
Did you type the entire sequence with the wpa_supplicant.conf file?

---

