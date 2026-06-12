---
title: "Connected but no wifi or wired internet connection"
date: 2014-01-15
forum: Networking &amp; Wireless
---

### Post by samo3 on 2014-01-15
Hi there,

I have tried installing Ubuntu 13.10 64-bit, 12.04 64-bit and 12.04 32-bit, and every time the same thing happens. During install I have a wired connection and updates are made. I also have internet connection the first time I run Ubuntu. But very randomly I loose internet connection, sometimes after close down, sometimes after sleep mode. I have tried alot of different solutions but none of them is stable.

If I can get any kind of ideas or hints about what could cause this problem, then I would really appreciate it,

```
uname -a
Linux juli 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux
```

```
lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 130 [8086:0896] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 130 BGN [8086:5005]
    Kernel driver in use: iwlwifi
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c604]
    Kernel driver in use: r8169
```


```
iwconfig
wlan0     IEEE 802.11bgn  ESSID:"o2-WLAN54"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 84:9C:A6:30:C5:7A   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:21   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```


```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E8:11:32:79:B9:0F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [o2-WLAN54] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        DC:A9:71:1B:85:5A

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *o2-WLAN54:      Infra, 84:9C:A6:30:C5:7A, Freq 2447 MHz, Rate 54 Mb/s, Strength 68 WPA2

  IPv4 Settings:
    Address:         192.168.1.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 130
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 34
       serial: dc:a9:71:1b:85:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-29-generic firmware=18.168.6.1 ip=192.168.1.30 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:f7200000-f7201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:79:b9:0f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:c000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
```

---

### Post by praseodym on 2014-01-15
Check:
```

cat /etc/resolv.conf
ifconfig -a
```

---

### Post by samo3 on 2014-01-15
```
ifconfig -a
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 130
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 34
       serial: dc:a9:71:1b:85:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=iwlwifi  driverversion=3.8.0-29-generic firmware=18.168.6.1 ip=192.168.1.30  latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:f7200000-f7201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:79:b9:0f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half  firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
       resources: irq:40 ioport:c000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
```

```
cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search localdomain
```

---

### Post by praseodym on 2014-01-15
Deactivate the N-mode of the wireless driver (bug) and the power management:
```

echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off
```

---

### Post by samo3 on 2014-01-24
Hi there, 

I just want to tell that deactivation of the N-mode of the wireless drive and the power management just worked out fine.

Thanks for the help

/Samo

---

