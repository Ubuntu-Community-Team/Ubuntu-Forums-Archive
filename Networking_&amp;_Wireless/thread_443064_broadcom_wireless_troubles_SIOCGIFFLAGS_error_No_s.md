---
title: "broadcom wireless troubles SIOCGIFFLAGS error: No such device"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by 4agte on 2007-05-14
Ok so ive updated to 7.4 then my wireless dosent work (was previously working with ndiswrapper)

then i tried using the easy fix downloading bcm43xx thingy which i kinda got to work but then it stopped and i got the error SIOCGIFFLAGS error: No such device

Eventually i tried using ndiswrapper again but its still not working and now i cant see wlan0 at all..

ive searched and tried just about everything im definatley a noob to linux so im sure that has alot to do with it but hopefully someone can point me in the right direction

thanks in advance

---

### Post by 4agte on 2007-05-14
ok so i got the wireless light on and i can select to configure the networks but apart from that no joy

---

### Post by franky1029 on 2007-08-21
I too am having this exact same issue.  I have found no way to resolve this issue, save a reinstall...  Any body have a solution of some sort?

Thank you ahead of time,

Franky

---

### Post by franky1029 on 2007-08-21
Thought I should add that I'm using a Dell Latitude D600, running Fiesty, and lspci says:

```
 02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

and ndiswrapper -l shows:

```
bcmwl5 : driver installed
device (14E4:4320) present (alternate driver: bcm43xx)
```

Also in the device manager, it shows that it recognizes the Wireless controller, but there seems to be no Networking interface associated to it (and I know it used to be there...)

Network Monitor shows the connection, but as  stated earlier gives a SIOCGIFFLAGS error: No such device

---

