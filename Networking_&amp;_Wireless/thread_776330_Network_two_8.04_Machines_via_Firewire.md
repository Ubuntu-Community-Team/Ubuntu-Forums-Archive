---
title: "Network two 8.04 Machines via Firewire"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by RDProgrammer on 2008-04-30
I tried a search for this but mostly just get back XP-Ubuntu results. What I am trying to do is network two computers (a Desktop and a Laptop) via Firewire. Each is running 8.04. I am hoping to use Firewire because they are both wirelessly networked and it's quite slow to transfer 20+ GB over WiFi. What program/settings/commands should I use?

RDP

---

### Post by scorp123 on 2008-04-30
Try this here:
[http://howto.krisbuytaert.be/FireWireClustering/x57.html](http://howto.krisbuytaert.be/FireWireClustering/x57.html)

This is a guide for Fedora but basically the instructions should work for Ubuntu as well. e.g. to load the network module for Firewire you'd use this command on Ubuntu: ```
sudo modprobe eth1394
```

If you check the number of interfaces again there should now be one more "eth*" interface: ```
sudo ifconfig -a
```

Now you can follow the rest of the guide above and use commands such as ...
```
sudo ifconfig eth1 10.0.139.1 netmask 255.255.255.0 up
``` ... to configure those new interfaces.

If you want to have the "eth1394" module (= device driver) load automagically at each system boot you'd have to modify this file: **/etc/modules**

In order to do that you'd type this into a terminal: ```
gksu gedit /etc/modules
``` ... and then make sure these lines are present (e.g. towards the end): 
```

sbp2
ieee1394
ohci1394
eth1394

```

Hope this helped ... :)

---

