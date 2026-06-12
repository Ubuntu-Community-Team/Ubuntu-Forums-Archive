---
title: "Wireless card names"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-04-07
I was wondering how wireless cards are sorted by name. It, my external atheros card is "ath0", my hardware network device is eth0, and internal Intel Pro/wireless card is eth1.

- What dictates which device is named what? 
- How can I change their names, if I want to? 
- How can I figure out which chipset each card is using? 
- Is "ethX" a catch-all category?

Thanks.

---

### Post by spd106 on 2007-04-07
I'm not completely sure about this however I believe the driver has first say in what the interface is named, then udev will assign an integer suffix. AthX is specific to the madwifi driver as it works only with Atheros based cards and has it's own wireless stack. 

You can also set a preference by editing the /etc/iftab to match a name to a mac address.

I have found that *sudo lshw -class network* is a good source of information as it lists the device name, interface name, driver used and lot's of other useful stats. The information it gathers is extracted from /proc/net.

The device manager is a useful gui based browser and don't forget lspci and lsusb.

---

### Post by IanW on 2007-04-07
If you enter (for example) "modinfo madwifi" into a terminal you will see near the bottom that the driver does have a say in what the interface is called as spd106 suspects.

From my own system:-
```
ian@Hex:~$ modinfo rt61
filename:       /lib/modules/2.6.17-11-generic/extra/rt61.ko
author:         http://rt2x00.serialmonkey.com
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS
license:        GPL
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
srcversion:     141B6AC581FFA719F76B5C5
parm:           ifname:Network device name (default ra%d) (charp)
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
```

Note the "parm: ifname:" line. It is here that the driver module tells the system what to call the interface - in my case "ra0" or "ra1" etc.

---

### Post by tturrisi on 2007-04-07
> - How can I figure out which chipset each card is using? 
The chipset is not "used", the chipset is built in to the device and chipset data is stored in ROM.  usually one needs to know the chipset of the device prior to building and installing the needed drivers for the device.  If the device is recognized by the kernel then the chipset can be identified by the command:
lshw -class network

To see what driver is required for a device once you know the chipset:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

