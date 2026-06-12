---
title: "Kubuntu 20.04.02 LTS doesn't recognize Ethernet adapter on DELL XPS 13 9360"
date: 2021-03-05
forum: Networking &amp; Wireless
---

### Post by nicolasduminil on 2021-03-05
Hello,

After having used during several years Windows on my DELL XPS 13 9360, I installed Kubuntu 20.04.02 LTS. But the Ethernet network adapter is not recognized. Here is the output of the lshw command:

```
[FONT=monospace][COLOR=#54ff54]**nicolas@nicolas-XPS-13-9360**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo lshw -C network [/COLOR]
  *-network                  
       description: Wireless interface 
       product: QCA6174 802.11ac Wireless Network Adapter 
       vendor: Qualcomm Atheros 
       physical id: 0 
       bus info: pci@0000:3a:00.0 
       logical name: wlp58s0 
       version: 32 
       serial: 9c:b6:d0:e0:98:c5 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.8.0-44-generic firmware=WLAN.RM.4.4.1-00140-QCARMSWPZ-1 ip=192.168.1.16 latency=0 link=yes multi
cast=yes wireless=IEEE 802.11 
       resources: irq:140 memory:dc000000-dc1fffff 
[COLOR=#54ff54]**nicolas@nicolas-XPS-13-9360**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

I have also a DELL XPS 15 9570 running exactly the same release of Kubuntu and Linux where the Ethernet adapter is recognized and works as expected. here is the same lshw command output on this machine:

```
[FONT=monospace][COLOR=#54ff54]**nicolas@nicolas-XPS-15-9570**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo lshw -C network [/COLOR]
[sudo] password for nicolas:  
  *-network                  
       description: Wireless interface 
       product: QCA6174 802.11ac Wireless Network Adapter 
       vendor: Qualcomm Atheros 
       physical id: 0 
       bus info: pci@0000:3b:00.0 
       logical name: wlp59s0 
       version: 32 
       serial: 9c:b6:d0:bd:37:95 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.4.0-66-generic fir
mware=WLAN.RM.4.4.1-00140-QCARMSWPZ-1 ip=192.168.1.21 latency=0 link=yes multicast=yes w
ireless=IEEE 802.11 
       resources: irq:149 memory:ed200000-ed3fffff 
  *-network 
       description: Ethernet interface 
       physical id: 2 
       bus info: usb@4:1.2 
       logical name: enxe4b97acb30ee 
       serial: e4:b9:7a:cb:30:ee 
       size: 1Gbit/s 
       capacity: 1Gbit/s 
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-
fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.10.
11 duplex=full ip=192.168.1.47 link=yes multicast=yes port=MII speed=1Gbit/s 
[COLOR=#54ff54]**nicolas@nicolas-XPS-15-9570**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

As one can see, the Ethernet adapter is recognized on XPS 15 but not on XPS 13. The dmesg command shows several errors on the XPS 13 (where it doesn't work) which don't appear on XPS 15 (where it works):

```
[FONT=monospace][COLOR=#18b218][   28.722230] [/COLOR][COLOR=#b26818]usb 4-1.2[/COLOR][COLOR=#b21818]: device not accepting address 4, error -62[/COLOR]
[COLOR=#18b218][   28.722403] [/COLOR][COLOR=#b26818]usb 4-1-port2[/COLOR][COLOR=#000000]: attempt power cycle [/COLOR]
[COLOR=#18b218][   34.146143] [/COLOR][COLOR=#b26818]xhci_hcd 0000:39:00.0[/COLOR][COLOR=#000000]**: Timeout while waiting for setup device command**[/COLOR]
[COLOR=#18b218][   39.522331] [/COLOR][COLOR=#b26818]xhci_hcd 0000:39:00.0[/COLOR][COLOR=#000000]**: Timeout while waiting for setup device command**[/COLOR]
[COLOR=#18b218][   39.730279] [/COLOR][COLOR=#b26818]usb 4-1.2[/COLOR][COLOR=#b21818]: device not accepting address 5, error -62[/COLOR]
[COLOR=#18b218][   45.148370] [/COLOR][COLOR=#b26818]xhci_hcd 0000:39:00.0[/COLOR][COLOR=#000000]**: Timeout while waiting for setup device command**[/COLOR]
[COLOR=#18b218][   47.744336] [/COLOR][COLOR=#b26818]logitech-hidpp-device 0003:046D:400A.0005[/COLOR][COLOR=#000000]: HID++ 2.0 device connected. [/COLOR]
[COLOR=#18b218][   50.519430] [/COLOR][COLOR=#b26818]xhci_hcd 0000:39:00.0[/COLOR][COLOR=#000000]**: Timeout while waiting for setup device command**[/COLOR]
[COLOR=#18b218][   50.727348] [/COLOR][COLOR=#b26818]usb 4-1.2[/COLOR][COLOR=#b21818]: device not accepting address 6, error -62[/COLOR]
[COLOR=#18b218][   50.727485] [/COLOR][COLOR=#b26818]usb 4-1-port2[/COLOR][COLOR=#b21818]: unable to enumerate USB device[/COLOR]
[COLOR=#18b218][   54.452146] [/COLOR][COLOR=#b26818]logitech-hidpp-device 0003:046D:404D.0006[/COLOR][COLOR=#000000]: HID++ 4.1 device connected. [/COLOR]
[COLOR=#18b218][  184.044433] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#000000]: AER: Corrected error received: 0000:00:1c.4 [/COLOR]
[COLOR=#18b218][  184.044450] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)[/COLOR]
[COLOR=#18b218][  184.044461] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:   device [8086:9d14] error status/mask=00001000/00002000[/COLOR]
[COLOR=#18b218][  184.044468] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:    [12] Timeout               [/COLOR]
[COLOR=#18b218][  308.975366] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#000000]: AER: Corrected error received: 0000:00:1c.4 [/COLOR]
[COLOR=#18b218][  308.975385] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)[/COLOR]
[COLOR=#18b218][  308.975398] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:   device [8086:9d14] error status/mask=00001000/00002000[/COLOR]
[COLOR=#18b218][  308.975407] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:    [12] Timeout               [/COLOR]
[COLOR=#18b218][  788.734260] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#000000]: AER: Corrected error received: 0000:00:1c.4 [/COLOR]
[COLOR=#18b218][  788.734277] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)[/COLOR]
[COLOR=#18b218][  788.734290] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:   device [8086:9d14] error status/mask=00001000/00002000[/COLOR]
[COLOR=#18b218][  788.734299] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:    [12] Timeout               [/COLOR]
[COLOR=#18b218][  998.711601] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#000000]: AER: Corrected error received: 0000:00:1c.4 [/COLOR]
[COLOR=#18b218][  998.711620] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)[/COLOR]
[COLOR=#18b218][  998.711633] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:   device [8086:9d14] error status/mask=00001000/00002000[/COLOR]
[COLOR=#18b218][  998.711641] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:    [12] Timeout               [/COLOR]
[COLOR=#18b218][ 1139.351598] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#000000]: AER: Corrected error received: 0000:00:1c.4 [/COLOR]
[COLOR=#18b218][ 1139.351616] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)[/COLOR]
[COLOR=#18b218][ 1139.351629] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:   device [8086:9d14] error status/mask=00001000/00002000[/COLOR]
[COLOR=#18b218][ 1139.351638] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:    [12] Timeout               [/COLOR]
[COLOR=#18b218][ 1650.256558] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#000000]: AER: Corrected error received: 0000:00:1c.4 [/COLOR]
[COLOR=#18b218][ 1650.256564] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)[/COLOR]
[COLOR=#18b218][ 1650.256566] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:   device [8086:9d14] error status/mask=00001000/00002000[/COLOR]
[COLOR=#18b218][ 1650.256568] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:    [12] Timeout               [/COLOR]
[COLOR=#18b218][ 2438.072729] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#000000]: AER: Corrected error received: 0000:00:1c.4 [/COLOR]
[COLOR=#18b218][ 2438.072746] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)[/COLOR]
[COLOR=#18b218][ 2438.072757] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:   device [8086:9d14] error status/mask=00001000/00002000[/COLOR]
[COLOR=#18b218][ 2438.072764] [/COLOR][COLOR=#b26818]pcieport 0000:00:1c.4[/COLOR][COLOR=#b21818]: AER:    [12] Timeout               [/COLOR]
[/FONT]
```

Based on some of the messages above, it seems that it would be a problem with usb:1:4:2 which is the bus info for the Ethernet adapter.

Also, the command modinfo displays the following for the r8152 driver on XPS 13:

```
[FONT=monospace][COLOR=#54ff54]**nicolas@nicolas-XPS-13-9360**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ modinfo r8152 [/COLOR]
filename:       /lib/modules/5.8.0-44-generic/kernel/drivers/net/usb/r8152.ko 
version:        v1.11.11 
license:        GPL 
description:    Realtek RTL8152/RTL8153 Based USB Ethernet Adapters 
author:         Realtek linux nic maintainers <nic_swsd@realtek.com> 
firmware:       rtl_nic/rtl8153b-2.fw 
firmware:       rtl_nic/rtl8153a-4.fw 
firmware:       rtl_nic/rtl8153a-3.fw 
firmware:       rtl_nic/rtl8153a-2.fw 
srcversion:     58993B03483707F434AA380 
alias:          usb:v2357p0601d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v2357p0601d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v0955p09FFd*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v0955p09FFd*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v13B1p0041d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v13B1p0041d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFpA387d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFpA387d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp7214d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp7214d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp720Cd*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp720Cd*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp7205d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp7205d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp3082d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp3082d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp3069d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp3069d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp3062d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp3062d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp304Fd*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp304Fd*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v04E8pA101d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v04E8pA101d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v045Ep0927d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v045Ep0927d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v045Ep07C6d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v045Ep07C6d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v045Ep07ABd*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v045Ep07ABd*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v0BDAp8153d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v0BDAp8153d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v0BDAp8152d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v0BDAp8152d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v0BDAp8050d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v0BDAp8050d*dc*dsc*dp*icFFisc*ip*in* 
depends:        mii 
retpoline:      Y 
intree:         Y 
name:           r8152 
vermagic:       5.8.0-44-generic SMP mod_unload  
sig_id:         PKCS#7 
signer:         Build time autogenerated kernel key 
sig_key:        5E:E8:D2:4A:45:82:CC:97:63:26:51:27:C3:AC:56:CF:F1:8A:9A:03 
sig_hashalgo:   sha512 
signature:      1E:69:1D:FE:38:8D:BD:3E:CF:19:AB:6A:2A:52:6F:FE:6A:45:EF:F8:
[/FONT]
```

The same command shows the following result on the XPS 15:

```
[FONT=monospace][COLOR=#54ff54]**nicolas@nicolas-XPS-15-9570**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ modinfo r8152 [/COLOR]
filename:       /lib/modules/5.4.0-66-generic/kernel/drivers/net/usb/r8152.ko 
version:        v1.10.11 
license:        GPL 
description:    Realtek RTL8152/RTL8153 Based USB Ethernet Adapters 
author:         Realtek linux nic maintainers <nic_swsd@realtek.com> 
srcversion:     B70E24833F524CCE291B132 
alias:          usb:v2357p0601d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v2357p0601d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v0955p09FFd*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v0955p09FFd*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v13B1p0041d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v13B1p0041d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFpA387d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFpA387d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp7214d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp7214d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp720Cd*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp720Cd*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp7205d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp7205d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp3082d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp3082d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp3069d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp3069d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp3062d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp3062d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v17EFp304Fd*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v17EFp304Fd*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v04E8pA101d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v04E8pA101d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v045Ep0927d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v045Ep0927d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v045Ep07C6d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v045Ep07C6d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v045Ep07ABd*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v045Ep07ABd*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v0BDAp8153d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v0BDAp8153d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v0BDAp8152d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v0BDAp8152d*dc*dsc*dp*icFFisc*ip*in* 
alias:          usb:v0BDAp8050d*dc*dsc*dp*ic02isc06ip00in* 
alias:          usb:v0BDAp8050d*dc*dsc*dp*icFFisc*ip*in* 
depends:        mii 
retpoline:      Y 
intree:         Y 
name:           r8152 
vermagic:       5.4.0-66-generic SMP mod_unload  
sig_id:         PKCS#7 
signer:         Build time autogenerated kernel key 
sig_key:        1E:07:0D:94:23:77:98:99:05:31:F3:76:E8:6B:76:12:7C:83:9E:05 
sig_hashalgo:   sha512 
signature:      5B:AB:A2:24:3D:ED:D9:9E:A2:B2:34:7B:F6:36:3F:39:D4:5D:60:B5:
[/FONT]
```

There are some differences between the two listings above but nothing of very important.

Could anyone please let me know what is happening here and how could I solve this issue ? I need to mention that the WIFI works as expected.

Many thanks in advance,

Nicolas

---

### Post by TheFu on 2021-03-05
Are you sure the assuption that both systems have identical NICs is valid?

---

### Post by praseodym on 2021-03-05
Please show
```

lspci -nnk
lsmod
```

---

