---
title: "Using dnsmasq on 14.04"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by cranerja on 2015-11-28
Hello, I am trying to use a machine running 14.04 with two Ethernet ports as a dhcp server. The first one for internet, and the second one to a switch as a dhcp server. I have followed different guides using dnsmasq and I am unable to connect to other machines. I have modified the config file for dnsmasq giving it a range, and configured eth1 manually. I am not on the machine at the moment, but assume I have similar configurations to this guide ignoring some parts: [http://www.danbishop.org/2015/01/30/ubuntu-14-04-ultimate-server-guide/](http://www.danbishop.org/2015/01/30/ubuntu-14-04-ultimate-server-guide/)

I also am running the desktop version rather than the server. If this impacts it, how do I go about it?

Thanks in advance

---

### Post by cranerja on 2015-11-28
I believe I have managed this by changing my tables. But now, neither of my samba shares and nfs' show on the network. How would I do that?

Edit: the computers on the network no longer see each other nor the server, even though they are being served ip addresses.

---

