---
title: "WMP54G Wireless PCI Adapter ubuntu server install - ANANDSUN"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by Anandsun on 2007-07-04
WMP54G Wireless PCI Adapter ubuntu server install 

--------------------------------------------------------------------------------

INSTALL ndiswrapper
sudo apt-get install ndiswrapper-utils

update will pause at 99% please be patient and let it complete
sudo apt-get update

Copy the Windows drivers for the card into a convenient directory.
They will include Rt61.INF and Rt61.sys and Rt61.cat files.
ndiswrapper -i Rt61.INF

To see them listed. One will have both driver AND hardware listed.
ndiswrapper -l

To see your wireless card listed. It won't be secured and will probably have 'any'as the essid.
iwlist ra0 scan

To set your wireless card up.
iwconfig ra0 essid youressid enc yourhexkey

Disable security on the wireless router. verify you are connected through the wireless router
ifup ra0


disconnect the wired ethernet cable and disable the interface
ifdown eth0


To see if it will mount.
ifconfig

If your wireless router issued you an IP address it will be listed by ifconfig. Make sure it didn't bind to your eth0 card instead.
If you are connected then issue
ndiswrapper -m


browse the internet.

---

