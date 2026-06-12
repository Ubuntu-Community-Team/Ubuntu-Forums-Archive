---
title: "wireless modes"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by bschleusner on 2007-01-22
Here's the problem. I am using kubuntu edgy, and I can't get it to network wirelessly. I think that it has something to do with the wireless mode because my usb network adapter, D-Link DWL-G120, can support 802.1b, and 802.1g. The problem is that it will not see the wireless g router. Is there a way I can cange it so that my adapter only scans for wireless G, and not wireless B?

Here is some stuff that I typed at the shell.](*,) 

brad@brad-desktop:~$ sudo ndiswrapper -l
prisma02 : driver installed      device (2001:3701) present (alternate driver: islsm_usb)
------------------------------------------------------------------------------- 
brad@brad-desktop:~$ sudo iwconfig eth2
eth2      IEEE 802.11b  ESSID:""
Mode:Auto  Channel=1  Access Point: Invalid
Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0 
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
--------------------------------------------------------------------------------
brad@brad-desktop:~$ sudo wlassistant
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
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
kdeinit: Can't connect to the X Server. 
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed! 
kded: ERROR: Communication problem with kded, it probably crashed.
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions. 
eth0      no wireless extensions.
sit0      no wireless extensions.
Wireless interface(s): eth2
Permissions checked.
ifconfig_status: /sbin/ifconfig eth2
scan: /sbin/iwlist eth2 scan
No networks found!

---

