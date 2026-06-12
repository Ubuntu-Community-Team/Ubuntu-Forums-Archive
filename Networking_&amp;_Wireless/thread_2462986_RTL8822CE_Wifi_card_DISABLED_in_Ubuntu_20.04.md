---
title: "RTL8822CE Wifi card DISABLED in Ubuntu 20.04"
date: 2021-05-31
forum: Networking &amp; Wireless
---

### Post by zean-7 on 2021-05-31
My Wifi has been having a lot of problems recently. It works for some time after I boot my system, but if I suspend my laptop or hibernate or sometimes even randomly, it stops working. I can still switch it on from the top-panel, but it just keeps scanning for networks and never displays any. Here's the output of ```
sudo lshw -c network
```:

```
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: 24:4b:fe:87:76:26
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.10.34-xanmod1 firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 ioport:e000(size=256) memory:fc904000-fc904fff memory:fc900000-fc903fff
  *-generic DISABLED
       description: Wireless interface
       product: RTL8822CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: ff
       serial: 80:30:49:3e:40:23
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822ce driverversion=5.10.34-xanmod1 firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11
       resources: irq:78 ioport:d000(size=256) memory:fc800000-fc80ffff
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: vethc626044
       serial: 92:7c:93:03:f4:dc
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=veth driverversion=1.0 duplex=full link=yes multicast=yes port=twisted pair speed=10Gbit/s
  *-network:1
       description: Ethernet interface
       physical id: 2
       bus info: usb@3:2
       logical name: usb0
       serial: c2:b2:8e:23:b3:c0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=5.10.34-xanmod1 firmware=RNDIS device ip=192.168.42.206 link=yes multicast=yes
```

Here, it can be seen that the network is shown as DISABLED(even when it's ON). I also noticed that whenever I turn on Wifi from the top-panel the journal logs that it failed to power on mac.

```
Jun 01 01:01:24 ThreadRipper kernel: rtw_8822ce 0000:03:00.0: failed to power on mac
Jun 01 01:01:24 ThreadRipper kernel: rtw_8822ce 0000:03:00.0: mac power on failed
Jun 01 01:01:24 ThreadRipper kernel: rtw_8822ce 0000:03:00.0: failed to poll offset=0x5 mask=0x2 value=0x0
Jun 01 01:01:24 ThreadRipper NetworkManager[183104]: <warn>  [1622489484.5831] platform-linux: do-change-link[3]: failure changing link: failure 114 (Operation already in progress)
Jun 01 01:01:22 ThreadRipper NetworkManager[183104]: <info>  [1622489482.5828] manager: rfkill: Wi-Fi now enabled by radio killswitch
Jun 01 01:01:22 ThreadRipper NetworkManager[183104]: <info>  [1622489482.5824] audit: op="radio-control" arg="wireless-enabled" pid=142839 uid=1000 result="success"
Jun 01 01:01:22 ThreadRipper kernel: rtw_8822ce 0000:03:00.0: failed to power on mac
Jun 01 01:01:22 ThreadRipper kernel: rtw_8822ce 0000:03:00.0: mac power on failed
Jun 01 01:01:22 ThreadRipper kernel: rtw_8822ce 0000:03:00.0: failed to poll offset=0x5 mask=0x2 value=0x0
Jun 01 01:01:22 ThreadRipper NetworkManager[183104]: <warn>  [1622489482.5823] platform-linux: do-change-link[3]: failure changing link: failure 114 (Operation already in progress)
Jun 01 01:01:20 ThreadRipper NetworkManager[183104]: <info>  [1622489480.5819] manager: rfkill: Wi-Fi hardware radio set enabled
```

I need a fix for this real bad. I've tried a lot of answers from various forums but none of them have helped me. :(

---

### Post by jeremy31 on 2021-05-31
Post results from terminal for ```
iwconfig; cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by zean-7 on 2021-05-31
```

iwconfig; cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf 

```

```

lo        no wireless extensions.


enp2s0    no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
docker0   no wireless extensions.


br-3437b7f38ea7  no wireless extensions.


br-bf54cea5b5d4  no wireless extensions.


vethc626044  no wireless extensions.


usb0      no wireless extensions.


[connection]
wifi.powersave = 2

```

---

### Post by chili555 on 2021-06-02
> driverversion=5.10.34-[COLOR="#FF0000"]xanmod[/COLOR]1I don't believe this is Ubuntu.

Please run and post:

```
lsb_release -a
```

---

### Post by zean-7 on 2021-06-02
```

lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

```

It is Ubuntu, but I am using a modified kernel, [http://xanmod.org](http://xanmod.org). The kernel version is
```

uname -r

5.10.32-xanmod1

```

The same issue is there if I use a mainline generic kernel.

---

