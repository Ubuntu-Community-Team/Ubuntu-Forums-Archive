---
title: "[SOLVED] wifi support"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by jatiesch on 2008-01-14
hi i could not enable my wifi connection....
i have AMD64 machine and gusty installed with a Netgear WG311v3 network card..

For ur support here is terminal output:

jatiesch@jatiesch-desktop:~$ sudo lshw -C network
*-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 7
bus info: pci@0000:01:07.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list
configuration: latency=64
jatiesch@jatiesch-desktop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

plz guide how to proceed so that i can run internet and use ubuntu to full potential
Thanks in advance...
_________________

---

### Post by wieman01 on 2008-01-15
The isn't working yet... Could you tell me what chipset the adapter is based on? Are you running the 64-bit version of Gutsy?

---

### Post by jatiesch on 2008-01-18
yup im running gusty for amd64

---

### Post by jatiesch on 2008-01-18
After going through given guide i got this....

[I]jatiesch@jatiesch-desktop:~$ lspci | grep Marvell
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

jatiesch@jatiesch-desktop:~$ ndiswrapper -h
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

jatiesch@jatiesch-desktop:~/CB-35P_3_1_1_7_Release/Inf/WinXP_2K$ ls
mrv8335.cat  mrv8335.inf  MRV8335NT.sys  MRV8335XP.sys
jatiesch@jatiesch-desktop:~/CB-35P_3_1_1_7_Release/Inf/WinXP_2K$ sudo ndiswrapper -i mrv8335.inf
installing mrv8335 ...

jatiesch@jatiesch-desktop:~$ ndiswrapper -l
mrv8335 : driver installed
        device (11AB:1FAA) present
jatiesch@jatiesch-desktop:~$ sudo modprobe ndiswrapper
jatiesch@jatiesch-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[/I]

so the problem continues..
plz help...

---

### Post by spmccann on 2008-01-18
If you can  connect over wired to the internet try using wifi radar
I had a similar problem and used this [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

---

### Post by wieman01 on 2008-01-19
What does a scan yield:
> sudo iwlist scan
And:
> sudo lshw -C network

---

