---
title: "Ndiswrapper doesn't create interface"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by smit0737 on 2006-08-08
I already have a PCI wifi card installed and working properly using ndiswrapper.  Months later, I am trying to drop that card and replace it with a USB wifi dongle.  The PCI card is an RTL8180 chipset based card.  My new USB dongle is a US Robotics USR805422.  Here's the basic outline I am using, however when I complete it, I don't see the expected wlan1 interface in my Networking Adminstration window:

Downloaded latest XP drivers
(Ndiswrapper-utils already installed through Synaptic)
```
sudo ndiswrapper -i RSC4USB.inf (in same directory as accompanying .sys file)
sudo ndiswrapper -l
```

at which point I get the following:

Installed ndis drivers:
net8180 driver present, hardware present
rsc4usb driver present, hardware present

```
sudo depmod -a
sudo modprobe ndiswrapper

```
but since ndiswrapper had already been inserted, dmseg | grep "ndiswrapper" doesn't show any new messages.

System->Administration->Networking shows my original wlan0, eth0 and ppp0 interfaces.  I expected to see a wlan1 in addition to these that I could configure.  I have uninstalled the rsc4usb drive with ndiswrapper -e a couple of times but get the same result each time.  In another attempt, I removed ndiswrapper with ```
sudo modprobe -r ndiswrapper
``` and then went through the procedure above again, but that didn't work either.

Any suggestions on what to try next?

---

