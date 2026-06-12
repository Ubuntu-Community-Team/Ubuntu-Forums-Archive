---
title: "Help with wireless DWL G122"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by BenHines on 2007-02-11
Hi,

I've done lots of reading of posts and finally have my ubuntu machine recognizing my D-Link DWL G122 USB adapter.  Doing an ndiswrapper -l gives the following:
netrtusb  : driver installed
usb55n5x  : driver installed
              device (07D1:3B01) present

All evidence suggests that the adapter is ready to go.  It is listed in the System->Adminsration->Networking tool.  It shows up in the ndiswrapper list. I see my wireless network when I run the Applications->Internet->Wireless Assistant.  However, the Wireless Assistant keeps failing to connect.  I also went through the steps necessary to connect from the command shell.  When I issue the dhclient command, it looks like it is trying to lease an IP address on both wlan0 and eth0 (eth0 doesn't have a cable hooked to it).  After some retries, it says: 

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any ideas on what is wrong?  I have another computer and a TiVo which both can connect wirelessly, so I know the router can accept wireless connections.  I even turned off the WEP security, but still no luck.

Thanks.

---

### Post by Floppyjoe on 2007-02-11
Possibly you need to disable your wired ethernet interface in System/Administration/Networking.
Don't have two or more interfaces active at the same time.

---

### Post by BenHines on 2007-02-12
I'll try this, but I don't think it is the issue because if I leave the wireless adapter on and hook up the wired NIC and do the dhclient, the wired card will lease an IP address successfully even though the wireless adapter exists.

Thanks for the response though.

---

