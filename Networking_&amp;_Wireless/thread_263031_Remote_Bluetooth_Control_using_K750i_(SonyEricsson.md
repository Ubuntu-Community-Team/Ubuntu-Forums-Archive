---
title: "Remote Bluetooth Control using K750i (SonyEricsson)"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by 8200 on 2006-09-22
Hi.

Does anyone know how I can use the remote control feature of my K750i with Ubuntu.

I can send and receive files, synchronize with Evolution (Multisync) but I can't use the remote control.

I have read that I only need to enable one option in /etc/default/bluez-utils

```
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.

HIDD_ENABLED=1
```

But this option doesn't help at all.



Thank you!

---

### Post by Ferrat on 2006-09-23
You can get it working without any major problems just search a little about bluetooth, HID and linux, however I haven't been able to set it so that my K750i can start the link, I have to do that from Linux and once I break it I have to restart it in Linux, haven't been able to find a working way to get Linux to respond and open the link automaticly when the phone tries to connect.

---

### Post by Ferrat on 2006-09-27
well go it working, wasn't that hard really =) 

just have Hid enabled like you done before and the at startup make ubuntu run 

$ sudo hidd --server 

then you should (or atleast I can connect without any problems when ever I want =)

so can everyone else with bluetooth I guess but anyway ;D

---

### Post by dave2010 on 2006-11-12
[http://www.ubuntuforums.org/search.php?searchid=9739159](http://www.ubuntuforums.org/search.php?searchid=9739159)

Look at that.
It's pathetic. Nothng helpful at all!
I'm hoping a zealot's righteous indignation that "Linux is ready for the desktop!!!" will prevail and provide us with a solution.

Please note: Every other question I have asked has been answered to a good standard or pointed me in the right direction.
Thanks,
Dave

---

### Post by nagyv on 2006-12-11
check out remotej

[http://sourceforge.net/projects/remotej/](http://sourceforge.net/projects/remotej/)

---

