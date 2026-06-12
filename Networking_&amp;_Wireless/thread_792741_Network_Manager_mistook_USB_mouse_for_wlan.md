---
title: "Network Manager mistook USB mouse for wlan?"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by Daneel24 on 2008-05-13
After connecting a USB mouse to my new laptop (Ubuntu 8.04) my wlan has completely disappeared, I can't find it in ifconfig (don't know if it was there before, but the wlan used to work!). Every time I connect the cable, I see a lot of the following in the System Log->debug:
> NetworkManager: <debug> nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_147e_1026_noserial').
EDIT: Never mind, the wlan disappearing was not related to the mouse after all... the error message is still curious though. 

My regular wired connection works sometimes... and sometimes I get an IP through DHCP, it shows up under ifconfig, but I can't connect to or ping anything. I get the following also in the system logs:
> NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

I'm not sure what wlan card/drivers I have but they are presumably ubuntu-compatible as the laptop was bought with Ubuntu installed. In the troubleshooting help it says to access System->Preferences->Hardware Information, but I have no such thing, not when editing the menus either. Just a "Hardware Drivers" for the Nvidia card. 

Any help on any of this would be appreciated, I'm not a complete newbie but I'm not sure what information would be helpful to provide.

---

