---
title: "D-Link USB Wi-Fi Adaptor installation problems in Xubuntu"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by voip4africa on 2007-08-14
Hi,

I;m using XUbuntu Edgy and got myself a D-Link DWL-G122 USB Wi-Fi Adaptor.
The unit came only with Windows drivers - nothing for Linux.
I connected the device to a USB port and under Applications >> Networking, I now see 2 wireless things listed:

Wireless Connection (wmaster 0)
This network interface is not connected

Wireless Connection (wlan 0)
This network interface is not connected

When I try to enable any of these, non of them shows any available networks ( even though my windows pc connects ok to the ones listed).

I went ahead and installed ndiswapper from the Synaptic Package manager but I don't see anywhere how to load &/or use it.

I went further and installed ndisgtk and now I see 'Windows Wireless Drivers' listed under Application >> System

However, when I load Windows Wireless Drivers, I see nothing listed under the 'Currently Installed Windows Drivers' box. I went to 'install new driver' and selected the NetRTUSB.inf and installed it, but nothing happens - it just returns to the 'Currently Installed Windows Drivers' and there's nothing listed there.


I re-unzipped the Windows drivers for the DWL-G122 device, this time to the /home/Administrator folder and Installed new driver under the Wireless Network Drivers.

No it shows (in the box of Currently Installed Windows Drivers):
netrtusb
Hardware present: No

Even though the hardware is presently connected to one of the USB ports. I even tried switching to a different USB port ad even restarting the PC, but no luck

Please help.

Best Regards.

---

