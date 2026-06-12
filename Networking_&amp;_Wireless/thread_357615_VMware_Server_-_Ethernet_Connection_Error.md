---
title: "VMware Server - Ethernet Connection Error"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by chipdip on 2007-02-09
Hello, VMware seems to be giving me some problems when I try to set up a Network Interface. When I boot the virtual machine I get an error:
```
Warning: Could not open /dev/vmnet8: No such file of directory.
Virtual device Ethernet0 will start disconnected.
```
I have included screenshots of the current VMware ethernet setup and error.

---

### Post by veloce on 2007-02-10
Did you set up networking when you installed VM Server?

On the host, does VMNet8 appear when you run ifconfig? If not, you'll have to reconfigure the virtual network settings.

Reconfiguring the virtual network settings is a pain in linux.  There's a nice gui in VM Server for windows that just isn't there for linux.  You have to run vmware-config (I think) and work through all the general stuff to get to the network stuff.

---

### Post by chipdip on 2007-02-11
Thank you, it was the configure script that I forgot. To anyone else that forgot, the script can be run by typing:
```
sudo /usr/bin/vmware-config.pl
```
into a terminal.

---

