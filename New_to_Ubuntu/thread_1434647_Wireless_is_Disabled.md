---
title: "Wireless is Disabled"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-03-20
I have a Dell Inspiron 1525, and I just installed a new hard drive for it. After reinstalling Windows and Ubuntu, I cannot seem to get the wireless working properly. If I click on the network icon at the top right of the screen, it says "wireless is disabled." Here's my output from sudo lshw -C network:

```

  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:de:fd:6f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth2
       version: 01
       serial: 00:1f:e1:c6:3f:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe7fc000-fe7fffff
john@EnigmaticLapux:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:de:fd:6f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth2
       version: 01
       serial: 00:1f:e1:c6:3f:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe7fc000-fe7fffff


```

What should I do?

P.S. It might be a hardware issue because I unplugged my wireless antennas when installing the hard drive, but I want to be absolutely certain that it's a hardware issue before disassembling my laptop again.

---

### Post by wojox on 2010-03-20
I've got BCM4312 802.11b/g and installed:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

After it installs reboot your computer and unplug your Ethernet cable. Then you should be able to log back on click nm-applet and see you're network.

---

### Post by Iowan on 2010-03-20
Wireless has an alias which *suggests* it is configured. You might check Network Manager to see if the eth2 setting is a problem (my laptop calls it eth1 instead of wlan0).

---

### Post by EnigmaticCoder on 2010-03-20
> **wojox said:**
> I've got BCM4312 802.11b/g and installed:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

After it installs reboot your computer and unplug your Ethernet cable. Then you should be able to log back on click nm-applet and see you're network.

I tried sudo apt-get update and it hung at 99%, so then I tried the second part of the command and it said that the newest version is already installed.

What is this network manager applet that you talk about? The icon at the top right?

"Wireless has an alias which suggests it is configured. You might check Network Manager to see if the eth2 setting is a problem (my laptop calls it eth1 instead of wlan0)."

All I see is eth0 and nothing else in wired network connections or wireless network connections (when I right click and hit edit connections).

---

### Post by bkratz on 2010-03-20
Since it is a Dell you just might want to look at and post the output of

rfkill list

---

### Post by wojox on 2010-03-20
> **EnigmaticCoder said:**
> 
What is this network manager applet that you talk about? The icon at the top right?


Yes. Did you disconnect the Ethernet cable and reboot?

---

### Post by EnigmaticCoder on 2010-03-20
Running rfkill list helped. The output told me there was a hardware block, so I looked for a switch (that I was unaware of) and toggled wireless back on.

I still cannot connect wirelessly, however, it says connection established and 100%, but I cannot load any webpages. I'm going to try to get this working on Windows first, but I'll log back onto Ubuntu later.

---

### Post by EnigmaticCoder on 2010-03-20
Well, I got wireless to work on Windows, so I know it's not a hardware problem, but I still cannot get it to work on Ubuntu. The network manager says that it's connected to my network and that it's at 100%, but when I open my browser, no website will load. Any ideas?

---

### Post by EnigmaticCoder on 2010-03-20
I managed to get it to work. In network manager, there were two entries for my network, I deleted the first entry and tried the second entry, and it worked.

---

