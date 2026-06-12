---
title: "Newb having problems with his dad's Emachines E725"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by natescape on 2014-07-03
Hi All,

I'm trying to install Ubuntu (latest version) on my dad's Emachines E725 laptop. It's all installed, but wifi ain't working, and I don't know how to do so. I'm a Ubuntu newbie, and would appreciate your help. I've googled it and found some solutions, but it's all Latin to me. 

Thanks,
Nate

---

### Post by yancek on 2014-07-04
There is an icon in the extreme upper right of the Desktop.  Click it and you should see available networks.  You can also select Edit connections and add a connections there.  You can also access network from the System Settings icon in the panel on the left, the gear shaped icon.  If you've tried this, you will need to post more detail on what you have done and what happened.

---

### Post by Bucky Ball on 2014-07-04
Please open a terminal and issue this command:

```
sudo lshw -C network
```

Post the output here, thanks.

---

### Post by natescape on 2014-07-05
Thanks folks!

There aren't any networks when I click the settings icon in the upper-right. No mention of networks at all.

Here's what I get from the sudo lshw -C network:
```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d4600000-d4603fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:11:4e:bf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=10.0.1.26 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:d3500000-d353ffff ioport:1000(size=128)
```

The wifi definitely worked when he had Windows installed on the system.

---

### Post by natescape on 2014-07-05
I figured it out. There was no driver installed for the Broadcom wifi, so I needed to install that through the Software and Updates section of the settings area. It's all good now. Thank you all for your help!

---

### Post by Iowan on 2014-07-05
When you're satisfied that the problem is fixed, please mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

