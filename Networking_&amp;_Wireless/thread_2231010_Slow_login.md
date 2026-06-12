---
title: "Slow login"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by AbdRahim on 2014-06-22
After logging out with networking disabled, there is a very slow login. The login hangs for many minutes.. 
Syslog:    [163347.092247] nfs: server xxx.xxx.xxx.xxx not responding, still trying. Login is normal if networking is enabled.

---

### Post by ibjsb4 on 2014-06-23
Slow boot without internet connection?  What works for me ..

Open /etc/network/interfaces and comment out eth0.
> ~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR=#ff0000]#auto eth0
#iface eth0 inet dhcp[/COLOR]
This will not effect your wired/wireless internet connection.  It will just speed up the boot time when internet is not present.

---

