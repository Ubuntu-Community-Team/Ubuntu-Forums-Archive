---
title: "Ubuntu 7.10 suddenly unable to connect"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by benbacardi on 2007-11-13
When I installed Ubuntu 7.10 on my laptop, it worked fine on my University's wireless system. However, one day, it suddenly stopped working and I don't know why. The gnome network applet shows the two grey dots with the spinning blue thing, but neither dot turns green and it won't connect. It just says "Attempting to join the wireless network" for ages but then just stops and returns to the "No network connection" symbol.

My wireless still works at my house, yet not on the University wireless. The University's wireless settings can be found [here](http://www.port.ac.uk/special/is/mobilemedia/broadband/wirelessoncampus/QuickReferenceGuide/).

I watched the messages log (/var/log/messages) as it tried to connect and I get following:

```
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
```

Any help much appreciated!!

---

