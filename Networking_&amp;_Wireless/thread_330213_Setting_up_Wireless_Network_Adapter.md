---
title: "Setting up Wireless Network Adapter"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by clemkonan on 2007-01-02
Is there a comprehensive guide to setting  up the Linksys WUSB54G ver 4 to work with 6.10 - the Edgy Eft..   

Thanks

---

### Post by jamesstansell on 2007-01-02
Besides the sticky in this forum and the How-To forum there's [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

The short summary

1. unsecure just needs your SSID in /etc/network/interfaces (network manager can write the file)

2. WEP isn't very secure, but just needs your key information added to /etc/network/interfaces .

3. WPA can take quite a bit to set up, especially the first time.

I'm still working on WPA with WUSB54G ver 4 to work with 6.10.  It looks like either use ndiswrapper with wpa_supplicant or use the built-in rt2570 driver with rutilt.  I'll post on this forum if I ever get it sorted out.  I'd prefer to use the built-in driver if possible.

HTH,

-james.

---

### Post by jamesstansell on 2007-01-02
I almost forgot.  With the rt2570 driver in edgy (and dappper too I think) don't use network manager to configure and activate the rausb0 interface at the same time.

Configure it first, then close network manager.  Then re-open network manager to activate the interface, or just use "sudo ifup rausb0".

The system will lock and require a hard reboot otherwise.

[https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/34902](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/34902)

Regards,

-james.

---

### Post by clemkonan on 2007-01-03
Thanks and yes I was trying to use Network Manager as a stand alone and getting no where

---

