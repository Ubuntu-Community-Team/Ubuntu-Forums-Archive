---
title: "Problem with network-manager on Broadcom 4318 with ndiswrapper"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by mar29 on 2006-12-23
Hi
I've upgraded from Dapper to Edgy (may have to go back :( )

I installed ndisgtk, knetworkmanager and downloaded 80211g.zip (32bit version) and have installed the drivers on my Asus A6Km laptop which has the Broadcom bcm4318.

I have another laptop, MSI S271 and I got wireless set up easily so I've done this all before and on Edgy.

I've blacklisted bcm43xx
I've checked ndiswrapper by typing ndiswrapper -l and it states:
bcmwl5 driver installed, hardware present.
(I've also tried bcmwl5a.inf and the same happens)

All is good until I load knetworkmanager. I get the following:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

and when I click the icon it tells me no network devices found.

This worked fine under Dapper and don't understand what is going on.
If you need any further info to work this out please tell me what to output I'm still a little new to linux.

Cheers in advance
Mark

---

