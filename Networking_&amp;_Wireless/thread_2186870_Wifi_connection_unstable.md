---
title: "Wifi connection unstable"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by lebon.sylvain on 2013-11-09
Hello,

I'm having a hard time with a wifi connection on Ubuntu 11.10 with a laptop with wifi integrated. The weird thing is that all other computers work fine on that wifi network, and this computer works fine with all other networks.
The connection gets randomly slower, sometimes even disconnecting. Then it can work fine for a few minutes or a few seconds.

```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: bc:77:37:aa:4f:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-32-generic firmware=17.168.5.1 build 33993 ip=192.168.0.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:42 memory:f7d00000-f7d01fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 00:90:f5:c1:fc:fe
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:f7c20000-f7c23fff ioport:e100(size=128) ioport:e000(size=256) memory:f7c10000-f7c1ffff memory:f7c00000-f7c0ffff

```

I tried
```

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1

```
and the situation gets a little better, but still disconnecting randomly.

I disabled IPV6 in /etc/default/grub with
```

GRUB_CMDLINE_LINUX="ipv6.disable=1"

```
and did an update-grub.

I also tried ```
sudo iwconfig wlan0 power off
``` but it didn't look like it changed anything.

dmesg gives this message regularly, which I presume to be linked to my issue.
```

[17428.245315] wlan0: authenticate with 96:b2:69:fd:95:04 (try 1)
[17428.252190] wlan0: authenticated
[17428.266305] wlan0: associate with 96:b2:69:fd:95:04 (try 1)
[17428.269055] wlan0: RX ReassocResp from 96:b2:69:fd:95:04 (capab=0x411 status=0 aid=2)
[17428.269058] wlan0: associated
[17428.275952] wlan0: deauthenticated from 96:b2:69:fd:95:04 (Reason: 6)
[17428.334352] cfg80211: All devices are disconnected, going to restore regulatory settings
[17428.334357] cfg80211: Restoring regulatory settings
[17428.334361] cfg80211: Calling CRDA to update world regulatory domain
[17428.337117] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[17428.337120] cfg80211: World regulatory domain updated:
[17428.337122] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[17428.337125] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[17428.337128] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[17428.337131] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[17428.337133] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[17428.337136] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[17429.143951] wlan0: authenticate with 96:b2:69:fd:95:04 (try 1)
[17429.148820] wlan0: authenticated
[17429.150103] wlan0: associate with 96:b2:69:fd:95:04 (try 1)
[17429.158516] wlan0: RX ReassocResp from 96:b2:69:fd:95:04 (capab=0x411 status=0 aid=2)
[17429.158520] wlan0: associated
[17430.410329] /dev/vmnet: open called by PID 1651 (vmnet-bridge)
[17430.410340] /dev/vmnet: hub 0 does not exist, allocating memory.
[17430.410358] /dev/vmnet: port on hub 0 successfully opened
[17430.410369] bridge-wlan0: device is wireless, enabling SMAC
[17430.410372] bridge-wlan0: up
[17430.410375] bridge-wlan0: attached
[17430.610181] userif-3: sent link down event.
[17430.610185] userif-3: sent link up event.

```
Any idea on how to diagnose my problem?
Thanks!

---

### Post by varunendra on 2013-11-11
Welcome to the forums lebon.sylvain!

We can try troubleshooting it, but it would make much more sense if we do it on a supported version. 11.10 has reached its EOL ([End Of Life]("https://wiki.ubuntu.com/Releases")). You should upgrade to 12.04.3 or 13.10. I'd recommend to download them via [torrent]("http://www.ubuntu.com/download/desktop/alternative-downloads") and try in live mode to see if it works fine on your system. If it does, do a clean install of it.

---

