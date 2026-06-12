---
title: "Won't connect to network."
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Nirevus on 2008-05-19
I have Ubuntu 8.04 installed on my mums laptop, up until the update to 8.04 the wireless card worked fine. The drivers are installed through ndiswrapper and are still functioning fine, the card is detected and the network is detected.

Two other acer laptops connect to the network fine, one running 8.04 and one running Windows XP (neither use ndiswrapper for the driver however).

The laptop in question is a dual boot with Ubuntu and Windows, the card had previously stopped working in Windows although this didn't present a problem as she primarily uses Ubuntu. When it stopped working in Ubuntu, I put a USB wireless card in and this functioned for a while, until it physically broke (she soldered the contacts back together, but they came apart again after a couple of days.)

I reinstalled Windows from the Acer recovery partition and the built in network card started working in Windows again; however Ubuntu still won't connect.

It finds the network, and has a fairly good signal strength, however it just can't connect, neither of the orbs on the connection indicator turn green and after several minutes the password box will pop up asking me to input the password for the network (by default this is saved on the keyring) it only offers the choice of either WPA Personal or LEAP (the network uses WPA2) and entering the connect password just gets it to search again for a while, before again prompting for a password.

Not sure what to do now, "ndiswrapper -l" in console reports the driver and device to be functioning correctly, and it does pick up the network, it just can't connect.

Any ideas?

---

### Post by Nirevus on 2008-05-20
Anyone?

---

