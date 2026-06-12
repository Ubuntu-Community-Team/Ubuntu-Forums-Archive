---
title: "ETHERNET NOT WORKING ON 13.10 - Intel 82552 10/100 Network [8086:10FE]"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by xbimma on 2014-03-08
I am having similar issue. wired network is not working after installing 13.10. wireless works (but too slow). I searched high and low the threads nothing worked! Can someone help. I posted the network information for diag:
```
uname -mr
3.11.0-12-generic i686

sudo lshw -numeric -C network -sanitize
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express) [168C:2B]
       vendor: Qualcomm Atheros [168C]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: [REMOVED]
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-12-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:febf0000-febfffff
  *-network DISABLED
       description: Ethernet interface
       product: 82552 10/100 Network Connection [8086:10FE]
       vendor: Intel Corporation [8086]
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: [REMOVED]
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:feaff000-feafffff ioport:ec00(size=64)
```

---

### Post by cariboo on 2014-03-09
Moved to a thread of it's own, as it is a different question from the one asked in the thread it was in.

---

### Post by varunendra on 2014-03-09
Thanks for the move cariboo !

@xbimma,
Your lshw output shows the Ethernet interface as **disabled** -
> **xbimma said:**
> 
```
  *-network **[COLOR="#FF0000"]DISABLED[/COLOR]**
       description: Ethernet interface
       product: 82552 10/100 Network Connection [8086:10FE]
```
Please try -
```
sudo ifconfig eth0 up
```

Does it activate the connection lights? If not, check your cables and physical connections, and also make sure that the Ethernet does not appear as 'Disabled' in lshw output after running the above command.

If the above command can not enable it, and _IF it is NOT a UEFI based installation_, try resetting BIOS to defaults and recheck Ethernet status.

Also, let me know what is your priority - the Ethernet or the Wireless? We can address both, but it would be good to focus on any one at a time.

---

### Post by xbimma on 2014-03-09
Thanks for replying and sorry for breaking the protocol on threading. To make it clear I edited the title. Another piece of information that can clarify the situation is I run a dual boot Windows XP and Ubuntu 13.10. Ethernet and Wireless work perfectly on Windows XP. Only Wireless works in Ubuntu 13.10. The results of the suggested command is posted below (no light came on and the lshw output is still DISABLED for eth0). Many thanks in advance
$ sudo ifconfig eth0 up
SIOCSIFFLAGS: Resource temporarily unavailable

---

### Post by varunendra on 2014-03-10
Please install ethtool -
```
sudo apt-get install ethtool
```
Then post back the output of the following commands -
```
sudo ethtool eth0
dmesg | egrep -i 'e100|firm'
```

And check your BIOS, see if there is an option called "IOMMU" in there. Try changing its state if there is.

---

### Post by xbimma on 2014-03-10
varun here are the outputs:
```

$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 31
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: no

```
```

$ dmesg | egrep -i 'e100|firm'
[    0.120823] [Firmware Info]: PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] not reserved in ACPI motherboard resources
[    0.138233] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    1.600667] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.600677] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.629270] e100 0000:01:08.0 eth0: addr 0xfeaff000, irq 20, MAC addr REMOVED

```

For the BIOS option "IOMMU" I entered this command "sudo dmidecode | grep IOM" and it returned nothing, is that sufficient or should I access the BIOS to be sure?

Thanks

---

### Post by varunendra on 2014-03-10
IOMMU is a new beast for me. And from what it does and the way it does, I don't think it'll appear in dmidecode. So check the BIOS to be sure. If it is a Gigabyte motherboard, a new one, then it certainly will have this feature. Not sure about others.

And is the card still active in XP? Just by rebooting into it?

If yes, and if there is no IOMMU option in the BIOS, please try a lower speed to see if it can at least detect the link -
```
sudo ethtool -s eth0 speed 10 duplex full autoneg off
```
Then check again -
```
sudo ethtool eth0
```
Does it detect the link?

One more thing - Have you tried rebooting your router? If not, please try -
Power the router off (and disconnect from power source) > wait 4 minutes > power it on again.

This card and the driver are so generic that I am a bit surprised it is having problems. Sometimes a buggy firmware (either the router's or that of the NIC itself) can get stuck, especially in case of windows/Linux dual-boot. In that case, a full power cycle (with sufficient gap in between to let all power from the capacitors be drained) can do the trick.

---

### Post by xbimma on 2014-03-10
None of these actions worked. XP is working fine with ethernet and there is no sign of IOMMU in bios. I am currently performing a the system update automatically prompted. Since I have just upgraded to 13.10 I am hoping a fix will come through. Will let you know the results. I keep on researching on my end.

---

### Post by xbimma on 2014-03-10
varun! the system update did the trick. After the restart ethernet is detected and working. thanks for your help on this.

---

### Post by varunendra on 2014-03-10
**EDIT:** Nevermind, Just noticed your second post, AFTER seeing the [SOLVED] prefix :p

[COLOR="#696969"]
Was the Ethernet working with Live DVD/USB? Can you try it in a Live session again?

There seems to be a sudden increase in Ethernet issues with all kind of adapters. So it may be related to some problematic update. If so, maybe another will fix it as well. But in that case, a Live session (in other words, the original kernel that came with 13.10) should work too.[/COLOR]

---

