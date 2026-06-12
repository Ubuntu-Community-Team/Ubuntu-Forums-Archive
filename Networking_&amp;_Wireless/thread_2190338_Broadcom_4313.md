---
title: "Broadcom 4313"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by Rocket2DMn on 2013-11-26
OK, so I've been banging my head against this and I can't seem to get it right.  When using the brcmsmac driver, my connection often cuts out under load (wireless icon still shows connected, just can't get anything).  If I'm downloading, the downloaded freezes, and I can't ping google or open new websites.  The connection returns after a minute or so, but it's becoming a huge headache.

The computer is a Dell Latitude E5530.  I'm using Xubuntu 13.10 with kernel 3.11.0-13-generic.

lspci -vnn:
```

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0015]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7e00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-56-ff-ff-c2-bc-85
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: bcma-pci-bridge

```

lshw -C network:
```

  *-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f7e00000-f7e03fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 10
       serial: f0:1f:af:1f:01:06
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 firmware=5761-v3.80 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f7c10000-f7c1ffff memory:f7c00000-f7c0ffff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: bc:85:56:c2:06:17
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.11.0-13-generic firmware=610.812 ip=192.168.1.101 link=yes multicast=yes wireless=IEEE 802.11bgn

```

In dmesg I get lines like
```
[ 1275.634005] brcmsmac bcma0:0: START: tid 1 is not agg'able
```

I blacklisted b43 and ssb in /etc/modprobe.d/blacklist.conf, though it doesn't seem to help. Here is "lsmod | grep brcm":
```

brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              596969  1 brcmsmac
cfg80211              479757  2 brcmsmac,mac80211
bcma                   46670  2 brcmsmac

```

The proprietary driver bcmwl-kernel-source (currently version 6.30.223.141+bdcom-0ubuntu1 - I've been unable to get an older one to work) functions OK for awhile, but eventually drops the connection altogether and I can't get it back without rebooting.

I've seen many threads and bug reports, but always end up back where I started.  I don't care which driver I use, as long as it works consistently.  Any help is appreciated.  Thanks.

---

### Post by Rocket2DMn on 2013-11-28
bump

---

### Post by heir4c on 2013-11-28
This is the only 2 I can give you to help you out. I have not a Broadcom so I can't help you further:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

---

