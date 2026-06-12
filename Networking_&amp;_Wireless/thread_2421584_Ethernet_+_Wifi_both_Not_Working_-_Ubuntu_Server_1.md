---
title: "Ethernet + Wifi both Not Working - Ubuntu Server 16.04 LTS"
date: 2019-06-24
forum: Networking &amp; Wireless
---

### Post by ahmedwaqas92 on 2019-06-24
Hello all,
Complete Newbie here!

Recently I installed a Ubuntu Server 16.04 LTS on a Lenovo S110 Ideapad netbook. The installation and everything went well however I cannot connect to my network (and the internet) through either the Ethernet or the WiFi. Can someone please tell me what exactly is wrong with the below configurations - All of the below tests were made with the Ethernet cable plugged in.

```

ping 192.168.0.1 (router address)
connect: Network is unreachable

```

```

ping www.google.com
ping: unknown host www.google.com

```

ifconfig
```

lo            Link encap:Local loopback
            inet addr:127.0.0.1 Mask: 255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:65536 Metric:1
            RX packets:966 errors:0 dropped:0 overruns:0 frame:0
            TX packets:966 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1
            RX bytes:86962 (86.9 KB) TX bytes:86962 (86.9 KB)


virbr0        Link encap: Ehternet HWaddr 52:54:00:6e:02:2f
            inet addr:192.168.122.1 Bcast: 192.168.122.255 Mask: 255.255.255.0
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 KB) TX bytes:0 (0.0 KB)

```



iwconfig
```

virbr0-nic        no wireless extensions.


lo            no wireless extensions.


virbr0        no wireless extensions.


emp1s0        no wireless extensions.


wlp2s0         IEEE 802.11bgn ESSID:off/any
            Mode: Managed Access Point: Not-Associated Tx-Power=0 dBm
            Retry short limit:7     RTS thr=2347 B     Fragment thr:off
            Power Management:on

```



sudo lspci -v
```

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 05)
               Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
               Flags: bus meter, fast devsel, latency 0, IRQ 27
               I/O ports at 4000 [size=256]
               Memory at 80004000 (64 bit, perfetchable) [size=4K]
               Memory at 80000000 (64 bit, perfetchable) [size=16K]
               Capabilities: [40] Power Management version 3
               Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit*
               Capabilities: [70] Express Endpoint, MSI 01
               Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
               Capabilities: [d0] Vital Product Data
               Capabilities: [100] Advance Error Reporting
               Capabilities: [140] Virtual Channel
               Capabilities: [160] Device Serial Number df-b2-00-00-36-4c-e0-00
               Kernal driver in use: r8169
               Kernal modules: r8169


02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n Wifi Adapter (rev 01)
               Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n Wifi Adapter
               Flags: bus meter, fast devsel, latency 0, IRQ 17
               I/O ports at 3000 [size=256]
               Memory at 84000000 (64 bit, non-perfetchable) [size=16K]
               Capabilities: [40] Power Management version 3
               Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit*
               Capabilities: [70] Express Endpoint, MSI 00
               Capabilities: [100] Advance Error Reporting
               Capabilities: [140] Virtual Channel
               Capabilities: [160] Device Serial Number 01-91-81-fe-ff-4c-e0-00
               Kernal driver in use: rt18192ce
               Kernal modules: rt18192ce

```



sudo lshw -C network
```

*-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n Wifi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: 00:1c:7b:db:e4:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt18192ce driverversion=4.4.0-151-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 ioport:3000(size=256) memory:84000000-84003fff
*-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: virbr0-nic
       serial: 52:54:00:6e:02:2f
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s

```


cat /etc/network/interfaces
```

# The Loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto emp1s0
iface emp1s0 inet dhcp
# This is an autoconfigured IPv6 interface
iface emp1s0 inet6 auto

```


sudo rfkill list
```

0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```


I would really appreciate if someone can assist and let me know on how I can get my network and internet running on both the Ethernet and WiFi for this Ubuntu Server 16.04! Thanks!

---

