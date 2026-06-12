---
title: "Compatibility of 3COM 3CSOHO100B with Ubuntu?"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by airandfingers on 2008-07-17
Hi, I am using the latest (stable) version of Ubuntu (Hardy Heron?), and I want to know if the 3COM 3CSOHO100B card is supported at all. I have plugged it into my machine with no results (does not show with ifconfig or any other commands I have seen suggested in this forum).

Link to 3COM's page: [http://www.3com.com/products/en_US/detail.jsp?tab=features&pathtype=purchase&sku=3CSOHO100B-TX](http://www.3com.com/products/en_US/detail.jsp?tab=features&pathtype=purchase&sku=3CSOHO100B-TX)

If it is supported or can be made to work, I'd like some help setting it up.. But if it will take too long, I would probably prefer to get a new one (I'm at work, so they have a bunch of different cards lying around.) By the way, this is the second ethernet card for this machine (the first is on-board).

Thanks!
Aaron

---

### Post by chili555 on 2008-07-17
Try this:```
sudo modprobe 3c59x
sudo lshw -C network
```Does your card show up with a driver (3c59x) and logical name (eth0) now?

---

### Post by airandfingers on 2008-07-17
The modprobe command did nothing, and the lshw command has only one entry--the onboard NIC-- which has the logical name "eth0".

I think I'm doing this right - just plugging the ethernet card into the spot it fits (a COM port?) and turning on the machine, but tell me if I'm supposed to do anything different.

Also, the ethernet cable is not plugged into the machine right now.. tell me if that's important at any point.

Thanks for the quick reply!

---

