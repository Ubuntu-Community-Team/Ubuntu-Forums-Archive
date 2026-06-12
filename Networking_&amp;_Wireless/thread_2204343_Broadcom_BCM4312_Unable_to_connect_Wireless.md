---
title: "Broadcom BCM4312: Unable to connect Wireless"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by Vu_Hoang_Minh on 2014-02-08
I'm using Dell Inspiron 1420, ubuntu 12.04. [ATTACH=CONFIG]250180[/ATTACH][ATTACH=CONFIG]250181[/ATTACH] Here are 2 pictures, the first one shows that there is a proper wirelesscard. There should be a lot of wireless spots show up right now, but it shows Wireless Network Disconnected

---

### Post by Bucky Ball on 2014-02-08
Well, there is no security name in the second pic. What happens when you enter the correct details there?

Also, please provide the output of:

sudo lshw -C network

Although the STA driver is offered and enabled, it may not be the correct driver for that card. Can you get online with a cable?

---

### Post by Vu_Hoang_Minh on 2014-02-08
> **Bucky Ball said:**
> Well, there is no security name in the second pic. What happens when you enter the correct details there?

Also, please provide the output of:

sudo lshw -C network

Although the STA driver is offered and enabled, it may not be the correct driver for that card. Can you get online with a cable?
Here is the result:
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 00:16:44:b3:45:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:04:cc:08
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb v3.04 ip=10.0.0.107 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fe5f0000-fe5fffff
```

Well, there is no wifi show up while there should be a lot of them.

---

### Post by Bucky Ball on 2014-02-08
Can you get online with a cable? That will make fixing this easier. If you can, open a terminal and:

```
sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
```

Reboot and hopefully you'll get some joy.

If you can't get online with a cable on your computer to do the above, then look [HERE.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access")

---

### Post by Vu_Hoang_Minh on 2014-02-08
> **Bucky Ball said:**
> Can you get online with a cable? That will make fixing this easier. If you can, open a terminal and:

```
sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
```

Reboot and hopefully you'll get some joy.

If you can't get online with a cable on your computer to do the above, then look [HERE.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access")
I do have cable, but I type the 2 lines and restart but nothing happen.

---

### Post by Bucky Ball on 2014-02-08
You are hitting return after each? Silly question but need to ask. Open a terminal while you're online with the cable and:

```
sudo apt-get update 
```

[hit return, wait, when back at the cursor]

```
sudo modprobe -r wl
```

[hit return, wait, when back at the cursor]

```
sudo apt-get install firmware-b43-lpphy-installer
```

[hit return, wait, when back at cursor close and reboot with cable out]

Like that? If still not working, post the result of this:

```
sudo lshw -C network
```

... to see if the right driver has in fact installed.

---

### Post by Vu_Hoang_Minh on 2014-02-08
Here is the result
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 00:16:44:b3:45:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:04:cc:08
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb v3.04 ip=10.0.0.107 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fe5f0000-fe5fffff


```

Pretty sure I have installed it, then reboot
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-lpphy-installer is already the newest version.
The following package was automatically installed and is no longer required:
  libindicator-messages-status-provider1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 448 not upgraded.


```

---

### Post by Bucky Ball on 2014-02-08
Okay, you are way behind with updates/upgrades. You should be doing these at least once a week. Updates on Ubuntu are important. Not like Windows where you just ignore them until your ready, although that's not a good idea either. Your machine's performance can degrade and there can be security risks if you don't stay regular in Ubuntu.  

Firstly, do you still have the cable in or is wireless working? As you didn't mention it was, I'll presume it's not. 

Go into 'Additional Drivers' and disable the STA driver by unticking it then run these four commands, hitting return and waiting until you get back to a cursor after each, please:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo modprobe -r wl
```

This will NOT upgrade your machine to the next release, just update/upgrade what you already have in there. 

Reboot. Report back. ;)

Yes, it is reporting you have the correct driver install but I think it is being blocked byh

---

### Post by Vu_Hoang_Minh on 2014-02-09
SOLVED
I currently use cable.
I have upgraded the machine, as you said, and I get the wireless again.

---

