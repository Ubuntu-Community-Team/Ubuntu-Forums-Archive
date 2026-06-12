---
title: "Wi-Fi Stopped Working"
date: 2022-03-23
forum: Networking &amp; Wireless
---

### Post by bilkay on 2022-03-23
My wife's laptop (18.04) just decided not to connect to wi-fi. It does connect in Windows. Here's what shows up in syslog when I click on "enable networking":
```
Mar 23 09:05:02 Notebook NetworkManager[1008]: <info>  [1648040702.6583] manager: enable requested (sleeping: no  enabled: no)
Mar 23 09:05:02 Notebook NetworkManager[1008]: <info>  [1648040702.6584] device (eth0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'managed')
Mar 23 09:05:02 Notebook kernel: [ 1967.987469] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 23 09:05:02 Notebook NetworkManager[1008]: <info>  [1648040702.8837] device (wlan0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'managed')
Mar 23 09:05:02 Notebook kernel: [ 1968.210553] r8169 0000:08:00.0 eth0: link down
Mar 23 09:05:02 Notebook kernel: [ 1968.210630] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 23 09:05:02 Notebook NetworkManager[1008]: <info>  [1648040702.8855] manager: NetworkManager state is now DISCONNECTED
Mar 23 09:05:02 Notebook NetworkManager[1008]: <info>  [1648040702.8859] audit: op="networking-control" arg="on" pid=4881 uid=1000 result="success"
Mar 23 09:05:02 Notebook kernel: [ 1968.212822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 23 09:05:02 Notebook nm-applet[4881]: Can't set a parent on widget which has a parent

```

After looking through posts with similar problems, I ran the following:

```
$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```
After running "rfkill unblock all" I got:
```
$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

and this:
 ```
$ lshw -class network
  *-network DISABLED        
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 40:f0:2f:3c:f8:ee
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.15.0-169-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:c2500000-c257ffff memory:c2580000-c258ffff
  *-network
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 05
       serial: a0:1d:48:bd:55:a5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=10.200.1.134 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:2000(size=256) memory:c2404000-c2404fff memory:c2400000-c2403fff

```

I'm kind of at a loss here.

---

### Post by chili555 on 2022-03-23
> 1: hp-wifi: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]This typically means that the hardware switch or wifi key combination, Fn+F8 or some such, is set to disable the wireless radio. Please check.

---

### Post by bilkay on 2022-03-23
Aha! It turns out that I just wasn't hitting the F-12 button hard enough. I'm surprised that "airplane mode" would be carried over through shutdown/startup.

---

### Post by bilkay on 2022-03-23
Not sure this is really solved. On my laptop (also 18.04), if I press the "airplane mode" key, wi-fi goes off, but I can turn it back on from the task bar. On my wife's laptop, when the wi-fi was off, I couldn't turn it on from the task bar - the "Enable wi-fi" option wasn't active.

---

