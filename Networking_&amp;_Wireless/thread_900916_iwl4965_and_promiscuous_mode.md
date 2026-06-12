---
title: "iwl4965 and promiscuous mode"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by hjlane3 on 2008-08-25
I've been experimenting with setting up some network monitoring tools. And I'm having some trouble/confusion with promiscuous mode with wireless and monitoring packets.

My understanding, is that when a networking device is in promiscuous mode (ifconfig device promisc), it should receive all packets whether the packet is directed to that device or not. With wired networking, the router/switch needs to be able to replicate all traffic to a single specified port (or if you're using a standard hub, since all traffic is indiscriminately  anyway).

With wireless devices, since all the packets are broadcast anyway, a wireless device in promiscuous mode should pick up all wireless traffic on that SSID and channel, regardless of the target destination. 

However, when I fireup Wireshark/tcpdump and it sets my wireless device in promisc mode (does automatically, and I set manually with ifconfig, it only picks up traffic to/from my wireless device and network broadcasts.

Am I missing something?

Info:

# lsmod | grep iwl
iwl4965                96132  0
iwlcore                92996  1 iwl4965
mac80211              266112  2 iwl4965,iwlcore
cfg80211               40600  3 iwl4965,iwlcore,mac80211

2.6.24-21-generic

           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wmaster0
                version: 61
                serial: 00:1f:3b:37:a9:17
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 ip=192.168.1.108 latency=0 module=iwl4965 multicast=yes promiscuous=yes wireless=IEEE 802.11abgn

---

### Post by urk_nono on 2008-08-26
I have some problems activating my intel Wifi 4965 on my new dv5-1095 laptop. If you have some hints on getting it up and running I'd greatly appreciate it :)

---

### Post by gradedcheese on 2008-08-26
I have my iwl4965 capturing (tested with wireshark).  I'm using the latest driver (now renamed iwlagn instead of iwl4965) and used iw to create a suitable monitor interface:

Assuming NetworkManager is not running and wmaster0 is the appropriate master interface and you want to capture on channel 6:

```
# iw dev wmaster0 interface add rtap0 type monitor
# ifconfig rtap0 up
# iwconfig rtap0 channel 7
```

To capture:

```

# wireshark -k -i rtap0

```

To get iw, you need to install libnl-dev and then build iw from source (copy its defconfig to .config and modify it as needed).  This also depends on you having headers for your (recent) kernel.  

The new iwlagn driver wanted the firmware image to be called iwlwifi-4965-2.ucode instead of iwlwifi-4965-1.ucode (I grabbed the latest from the Intel Linux wireless site and renamed it).  If you use a stock iwl4965 driver, that shouldn't be a problem.

---

