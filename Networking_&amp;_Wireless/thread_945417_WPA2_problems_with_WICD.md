---
title: "WPA2 problems with WICD"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by ubu123 on 2008-10-12
After a lot of frustration, I finally got my Dell Truemobile 1300(BCM4306 Rev. 2) working with ndiswrapper(I couldn't get fwcutter to work).  I found that I couldn't connect to my WPA2 network with network-manager, although I could connect to an open network.  I installed WICD as I had had better luck with that in the past.  It still will not connect, but gets stuck on None: Validating Authentication.  Once None was replaced by the name of my network, but it soon flashed back to None.  I have set the WPA supplicant driver to ndiswrapper.  Thanks in advance for any help.

---

### Post by kevdog on 2008-10-12
The wpa_supplicant driver is supposed to be wext.  If you take a look at manually configuring the connection (the link is in the stick), you will get an idea of the parameters.

---

### Post by ubu123 on 2008-10-13
Thanks, but by default it was set to wext.  That didn't work.  When I changed it to ndiswrapper, there was no difference.

---

