---
title: "Wireless Internet not Working"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by master_script_maker on 2008-10-30
Hi everyone!
I have Ubuntu 8.04 and my laptop is a hp pavilion zv5320us with an integrated broadcom wireless card. can someone help me with this?
Thanks

---

### Post by sir4taye on 2008-10-31
need more info. goto terminal and post results from lspci

---

### Post by el2king on 2008-10-31
Hello,

I am also having a wireless problem, where I can see my wireless card, but it doesn't show up in Network Manager of ifconfig.  Here is some output from running some commands:

sudo ndiswrapper -l:
    bcmwl5 : driver installed
        device (14E4:4328) present (alternate driver: wl)

sudo lspci:
    0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

sudo iwlist scanning:
    lo        Interface doesn't support scanning.
    eth0      Interface doesn't support scanning.
    pan0      Interface doesn't support scanning.

sudo lshw -C network:
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:c6:bf:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.109 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:69:87:b5:47:d4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

sudo dmesg:
[   16.014361] b43-phy0: Broadcom 4321 WLAN found
[   16.061063] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
[   16.061097] b43: probe of ssb0:0 failed with error -95
[   16.061135] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]

Under System -> Administration -> Hardware Drivers, I have the "wl" driver enabled and the "Broadcom B43 wireless driver" disabled.  Under System -> Administration -> Windows Wireless Drivers, I have the "bcmwl5" driver installed.  My computer is a Dell Inspiron E1505, and I upgraded from 8.04 to 8.10 earlier in the day.  Every other hardware device works as it did in 8.04, except for the wireless.  Also, I used this link to install the wireless driver for the 8.04 install, since wireless did not work out of the box then:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Any ideas at all from anyone?

Thanks,
Edward

---

### Post by el2king on 2008-10-31
Can anyone help me on this?  Thanks!

---

### Post by superprash2003 on 2008-10-31
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

