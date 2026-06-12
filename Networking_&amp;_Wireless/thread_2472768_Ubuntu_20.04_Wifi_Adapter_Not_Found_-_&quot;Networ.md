---
title: "Ubuntu 20.04 Wifi Adapter Not Found - &quot;Network DISABLED&quot;"
date: 2022-03-11
forum: Networking &amp; Wireless
---

### Post by p.s. on 2022-03-11
I replaced my wife's broken laptop with a Dell Latitude and installed Ubuntu Budgie 20.04 on it. It's been working great, but the battery is old. I ordered a replacement battery and installed it, and after that the wifi just stopped working. I've followed various tutorials for getting it fixed including restarting the network manager, checking networkmanager.state, checking the BIOs, editing network-manager-all.yaml (and then reverting it when it didn't help), etc. but have had no luck. The gui Wireless menu says "no wifi adapter found". lshw -C network shows "*-network DISABLED" above the wireless interface. I have two questions:

1. Anyone have thoughts on how to fix this? (I am a relatively competent command line user who's just too much of a layperson to diagnose things.)
2. I hot-swapped the battery on the latitude (and have done this many times with laptops). Could that have caused the problem?
```
1: cara@latitude:
cara@latitude: $ sudo systemctl start network-manager.service
cara@latitude: $ sudo iwconfig wlp2s0 up fiwconfig: unknown command "up"
gara@latitude:~$ lspci
0:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Grap
nics Controller (rev 09)
30:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1
(rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) (rev 04) 00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controlle - #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Control ler (rev 04) 00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4 )
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4 )
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controlle r #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04) 02:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless Network Adapter (re
v 01) 09:00.0 SD Host controller: 02 Micro, Inc, OZ600FJ0/0Z900FJ0/0Z600FJS SD/MMC Card Reader Controller (rev 05)
09:00.1 Mass storage controller: 02 Micro, Inc. Device 8231 (rev 03)
cara@latitude:~$
Default Applications
Windowing System

    product: PnP device PNPOC01
    physical id: 9
    capabilities: pnp
    configuration: driver-system
    WARNING: output may be incomplete or inaccurate, you should run this p
    cara@latitude:~$ iwconfig
    lo
    no wireless extensions.
    no wireless extensions.
    eno1
    wlp2s0
    IEEE 802.11 ESSIDff/any
    Mode: Managed Access Point: Not-Associated Retry short limit:7 RTS thrff Fragment thrff
    Power Management: off


    lshw -C network:


        physical id: 19
        bus info: pci@0000:00:19.0
        logical name: eno1
        version: 04
        serial: 84:8f:69:f1:70:a6
        capacity: 1Gbit/s width: 32 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd auton
        egotiation
        configuration: autonegotiation-on broadcast=yes driver=e1000e driverversion=5.13.0-30-generic ware-0.13-3 latency=0 link=no multicast=yes port=twisted pair
        resources: irq:30 memory:e1c00000-e1c1ffff memory:e1c80000-e1c80fff ipport: 3080(size=32)
        *-network DISABLED
        description: Wireless interface product: BCM4313 802.11bgn Wireless Network Adapter
        vendor: Broadcom Inc. and subsidiaries
        PU @
        ics 30
        Ubunt
        &#21697;
        physical id: 0
        bus info: pci@0000:02:00.0 logical name: wlp2s0
        version: 01
        serial: 74:de:2b:e3:02:0a
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver-wlo driverversion=6.30.223.271 (r587334) latency=0 multicast=y
        es wireless=IEEE 802.11
        resources: irg:17 memory:e1b00000-e1b03fff WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
        cara@latitude: /etc/netplan$ lshw -C network
        Default Applications
        Windowing System
        DELL
        firm 

```

---

### Post by wildmanne39 on 2022-03-11
Hello, I jailed your duplicate post, instead of starting a new thread in the future edit your post to add additional information instead please.

---

### Post by p.s. on 2022-03-12
EDIT: Disregard this, I think I misunderstood the reply.

I added what happened, what I did to try and resolve it, and the output of as many files/commands as I thought might be helpful. I apologize if my post is a duplicate but I've followed the instructions in other posts with similar issues and it still does not work. (Plus, my other question about the battery isn't a duplicate of anyone else's.) Could you please link me to a post you consider to be a duplicate?

---

### Post by chili555 on 2022-03-12
> *-network DISABLEDThat usually means that the hardware switch or key combination is set to turn off the wireless radio. You can verify it with the command:

```
rfkill list all
```

---

### Post by p.s. on 2022-03-13
That took care of it, thank you!

---

