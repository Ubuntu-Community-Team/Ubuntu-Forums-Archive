---
title: "Feisty broke my bluetooth"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by soy Keymaster on 2007-06-23
I had bluetooth working with my Motorola T305 BT speakerphone just fine in Edgy (on two different usb bluetooth dongles, no less).  I wiped the drive and did a fresh install of Feisty then copied the settings from hcid.conf over to the new install and suddenly it won't connect with either dongle.  It asked for a pin then did nothing.  Any subsequent "hcitool cc [btaddr]" commands cause the device to briefly connect then disconnect.  I ran "hcitool con" on a 0.1 sec interval to monitor what was happening.  Here is the output:

[directly after issuing the command this would show up and last for 1-3 seconds]
Connections:
        < ACL 00:0B:2E:93:4D:4C handle 12 state 1 lm MASTER

[it then changes to this which lasts for around 1 second ]
Connections:
        < ACL 00:0B:2E:93:4D:4C handle 12 state 8 lm MASTER

[about 3 times out of 10 this shows up 3-5 seconds after the above message disappears and lasts for only 0.1s]
Connections:
        < ACL 00:0B:2E:93:4D:4C handle 1 state 11 lm SLAVE

From what I can tell there are others having the same problem:
[http://ubuntuforums.org/showthread.php?t=480901](http://ubuntuforums.org/showthread.php?t=480901)
[http://ubuntuforums.org/showthread.php?t=475390](http://ubuntuforums.org/showthread.php?t=475390)

---

