---
title: "netgear wg111v2 usb with ndis, can anyone help?"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by ukmh on 2007-10-11
Stuck on this one: netgear wg111v2 usb on ubuntu 6.06, using ndiswrapper with ndisgtk. Followed the guide at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and can now see the adapter listed in device manager but cannot get it to communicate with router at all (all this stuff was recently working under windows so not a hardware issue + ssid/wep checked and double checked, mac filtering off for now just to be sure).
lsusb in terminal produces this: 

Bus 001 Device 012: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 0000:0000

and wlan0 appears in network settings (as active), system>administration>windows wireless drivers sees the device and has the settings.

The light on the wg111 flashes for a bit then stops, over and over, always the same pattern not irregular/frantic activity as I normally see when connecting/connected.

Would very much appreciate any help.

Thanks all.

UPDATE: Thanks for reading post but problem is now solved! Although more of a work around than a solution: switched to puppy linux which seems to be fast, full featured and (best of all) it was amazingly easy to get the wg111 working with it. Just installed puppy linux, clicked the connect icon on the desktop and followed the instructions. Did need to copy the drivers accross from netgear cd to a folder on hard drive but all simple. All done in less than an hour! Sorry to dedicated buntu fans but I've converted to puppy linux for good! :)

---

