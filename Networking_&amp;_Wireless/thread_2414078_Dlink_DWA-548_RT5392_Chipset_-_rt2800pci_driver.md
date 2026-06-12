---
title: "Dlink DWA-548 RT5392 Chipset - rt2800pci driver"
date: 2019-03-05
forum: Networking &amp; Wireless
---

### Post by jorge-f-am on 2019-03-05
[I]Hi guys!
I need help about the Dlink DWA-548 (Pci interface) with RT5392 Chipset and rt2800pci driver.
The Wi-fi card doesn't work, sometimes it seems that it will connect, it stays loading but never connects.
I have been reading this posts:
[/I]
[https://ubuntuforums.org/showthread.php?t=2230635&highlight=RALINK+RT5392](https://ubuntuforums.org/showthread.php?t=2230635&highlight=RALINK+RT5392)
[https://ubuntuforums.org/showthread.php?t=2071830](https://ubuntuforums.org/showthread.php?t=2071830)
[https://forums.linuxmint.com/viewtopic.php?t=257974](https://forums.linuxmint.com/viewtopic.php?t=257974)
[https://ubuntuforums.org/showthread.php?t=1815451&page=1&highlight=ralink+drivers](https://ubuntuforums.org/showthread.php?t=1815451&page=1&highlight=ralink+drivers)

*Also, I have tried with this commands (but still not working):*

**sudo lshw -C network**
```
*-network                 
       description: Wireless interface
       product: RT5392 PCIe Wireless Network Adapter
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: 54:b8:0a:01:0c:69
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.18.20-041820-generic firmware=0.40 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:29 memory:f7600000-f760ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 0c
       serial: e0:d5:5e:e4:b4:79
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:34 ioport:f000(size=256) memory:f7500000-f7500fff memory:f0000000-f0003fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp1s0f0u4
       serial: 4e:92:e1:cf:33:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.174 link=yes multicast=yes
```


**ifconfig**
```
enp1s0f0u4: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.42.174  netmask 255.255.255.0  broadcast 192.168.42.255
        inet6 fe80::5a50:55b1:e15b:5615  prefixlen 64  scopeid 0x20<link>
        ether 4e:92:e1:cf:33:b6  txqueuelen 1000  (Ethernet)
        RX packets 52233  bytes 52593781 (52.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 40403  bytes 6343941 (6.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether e0:d5:5e:e4:b4:79  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 11161  bytes 1069055 (1.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11161  bytes 1069055 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:b8:0a:01:0c:69  txqueuelen 1000  (Ethernet)
        RX packets 3917  bytes 5205400 (5.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2030  bytes 201409 (201.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

**iwconfig**
```
enp1s0f0u4  no wireless extensions.

enp4s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.
```

**lspci -nn | grep 0280**
```
03:00.0 Network controller [0280]: Ralink corp. RT5392 PCIe Wireless Network Adapter [1814:5392]
```

**lspci -nnk | grep -iA2 net**
```
03:00.0 Network controller [0280]: Ralink corp. RT5392 PCIe Wireless Network Adapter [1814:5392]
    Subsystem: D-Link System Inc RT5392 PCIe Wireless Network Adapter [1186:3c06]
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

**lspci -vvnn | grep Network**
```
03:00.0 Network controller [0280]: Ralink corp. RT5392 PCIe Wireless Network Adapter [1814:5392]
    Subsystem: D-Link System Inc RT5392 PCIe Wireless Network Adapter [1186:3c06]
```

**lspci -vvnn | grep -A 9 Network | grep Kernel**
```
Kernel driver in use: rt2800pci
Kernel modules: rt2800pci
```


**sudo modprobe rt2800pci**
**dmesg | grep rt2**
```
[   17.175187] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[   17.178792] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5392 detected
[   17.400570] rt2800pci 0000:03:00.0 wlp3s0: renamed from wlan0
[   32.715098] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   32.739018] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.40
[   54.680200] rt2800pci 0000:03:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x00000000ff968000 flags=0x0000]
[   55.384075] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   56.916176] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   57.516054] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   58.216054] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
```


*I tried this command, but I think there's nothing to delete (because I can't see/find a ndiswrapper folder in etc directory):*
[B]sudo rm -rf /etc/ndiswrapper/*

[/B]
[I]Thanks,

Jorge A.[/I]

---

### Post by praseodym on 2019-03-05
Try this one

```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
and reboot

---

