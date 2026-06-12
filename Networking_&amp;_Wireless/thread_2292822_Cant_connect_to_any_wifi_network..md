---
title: "Cant connect to any wifi network."
date: 2015-08-31
forum: Networking &amp; Wireless
---

### Post by spin-milt on 2015-08-31
Hello all,

I was playing Ryzom and my connection was unstable but suddenly the wifi disconnected and since then I cannot get it connect it back.
I have tried some commands I found at many forums but I am afraid that I messed up everything.
I am new and promising at unix systems but at the moment I am desperate.

Laptop:Lenovo G50

```

sudo iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
lo        no wireless extensions.

```

```

sudo lspci -v

03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 93)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160
	Flags: bus master, fast devsel, latency 0, IRQ 52
	Memory at d1100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [40] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number f4-06-69-ff-ff-5c-e6-ad
	Capabilities: [14c] Latency Tolerance Reporting
	Capabilities: [154] Vendor Specific Information: ID=cafe Rev=1 Len=014 <?>
	Kernel driver in use: iwlwifi

```
```

sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 68:f7:28:9c:b0:b2
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:4000(size=256) memory:d1204000-d1204fff memory:d1200000-d1203fff

```

---

### Post by chili555 on 2015-08-31
Let's check a couple of other things:```
cat /etc/modprobe.d/iwlwifi.conf
rfkill list all
iwconfig
```Thanks.

---

