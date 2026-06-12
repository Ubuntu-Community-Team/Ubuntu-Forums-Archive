---
title: "NAT/Port Forwarding?"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by winkerbean on 2007-09-10
Hi,
    I'm trying to set up NAT/Port Forwarding for Azureus.  I have in this order:
[INDENT]modem->router->Ubuntu box[/INDENT]
I know I need the 192.168.xxx.xxx address of my Ubuntu box for good NAT/Port Forwarding.  How do I find that address?

Thanks in advance.

---

### Post by spd106 on 2007-09-10
There are many places. 

Try right-clicking on nm-applet in the notification area (top-right toolbar) and select connection information. You can also access this information in the System -> Admin -> Network capplet if you have a static configuration.

From a terminal, try this command
```
ip address show
``` or just ```
ip a
``` or if you want to go old school ```
ifconfig
```

---

