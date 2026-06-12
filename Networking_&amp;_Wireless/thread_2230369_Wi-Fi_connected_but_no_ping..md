---
title: "Wi-Fi connected but no ping."
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by psc21990 on 2014-06-18
Hi! I am running Ubuntu 14.04 on my Samsung Ativ book 4. After random intervals (1 min to 4 hours), I get disconnected from the external internet. I mean Wi-Fi still stays connected, I can ping my router and localhost but cannot ping any external address by IP or URL. I am facing similar issues on my Arch setup as well.

Here's my ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 18:67:b0:df:3c:f0            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:518365 (518.3 KB)  TX bytes:518365 (518.3 KB)


wlan0     Link encap:Ethernet  HWaddr b4:b6:76:6c:19:66  
          inet addr:165.123.12.127  Bcast:165.123.13.255  Mask:255.255.254.0
          inet6 addr: 2607:f470:6:2007:9c71:ec36:cd52:487c/64 Scope:Global
          inet6 addr: fe80::b6b6:76ff:fe6c:1966/64 Scope:Link
          inet6 addr: 2607:f470:6:2007:b6b6:76ff:fe6c:1966/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:158271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204612980 (204.6 MB)  TX bytes:11742935 (11.7 MB)



```


lspci -k :
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)	Subsystem: Samsung Electronics Co Ltd Device c706
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: mei_me
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
	Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c706
01:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN
	Kernel driver in use: iwlwifi
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
	Subsystem: Samsung Electronics Co Ltd Device c706
	Kernel driver in use: r8169
```

What should I do to resolve this problem? 

Thanks in advance!

---

### Post by Bucky Ball on 2014-06-19
Welcome. Click the network icon and Edit Connections. Navigate to your wireless connection>IPv6 tab. Set it to 'Ignore'. Any different?

If not, please provide the output of this:

```
sudo lshw -C network
```

---

### Post by psc21990 on 2014-06-24
Thanks for the reply! 

I've already disabled IPv6 on Ubuntu but the problem still persists.

Here the output of : ```
sudo lshw -C network
``` :

```
*-network                      description: Wireless interface
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 24
       serial: b4:b6:76:6c:19:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=18.168.6.1 ip=158.130.221.65 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f7c00000-f7c01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 18:67:b0:df:3c:f0
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
```

---

### Post by William_Brennan on 2014-06-24
I noticed similar issues when I first installed 14.04 with my wireless. Turned out my issue was due to my wireless security. Ubuntu apparently doesn't play well with TKIP, so I changed it to AES, and it was a night and day difference. With TKIP I could download at BEST around 100 kbp/s, if I even got a connection. Check the settings in your router and see what you've got going on.

---

### Post by alpha2400c on 2014-06-25
How did you change it to AES? I have a similar issue concerning my router, and I am wondering if that is it.

---

