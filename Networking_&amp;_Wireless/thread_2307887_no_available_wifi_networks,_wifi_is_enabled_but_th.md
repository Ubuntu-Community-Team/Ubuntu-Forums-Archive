---
title: "no available wifi networks, wifi is enabled but the state is &quot;disconnected&quot;"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by derpyhooves2 on 2015-12-29
I am very new to Ubuntu, so, probably, the solution will be the simple one. And I would really appreciate if you will explain every step of your advices :)
Thank you in advance!


My problem is that the laptop doesn't see the Wi-Fi networks. However, everything was working before, but today the laptop freezed and I restarted it via R E I S U B pushing while hanging Alt+PrtSc.
 
The system version is Ubuntu 15.10, the laptop is Lenovo U31.


First I checked the NetworkManager Status:
```
>>> nmcli -p g
=================================================================
                      NetworkManager status
=================================================================
STATE         CONNECTIVITY  WIFI-HW  WIFI      WWAN-HW  WWAN    
-----------------------------------------------------------------
disconnected  none          enabled  disabled  enabled  enabled
```


Then I checked the blocks:
```
>>> rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```


I unblocked it (_rfkill unblock all_) and it worked: all Soft blocked became “no” and WIFI status became “enabled”. But the State is still disconnected.


The _lshw -C network_ cannot find my wireless device:
```
>>>  lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: 1c:39:47:1c:28:f6
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:3000(size=256) memory:c1204000-c1204fff memory:c1200000-c1203fff
  *-network
       description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 20
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ath10k_pci latency=0
       resources: irq:52 memory:c1000000-c11fffff
```


The WiFi seems to be enabled:
```
>>>  nmcli radio wifi
enabled
```


But the list of networks is empty:
```
>>> nmcli device wifi list
*<no result>*
```


The info about the hw:
```
>>> lspci -v
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Lenovo Device 3828
    Flags: bus master, fast devsel, latency 0, IRQ 47
    I/O ports at 3000 [size=256]
    Memory at c1204000 (64-bit, non-prefetchable) [size=4K]
    Memory at c1200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169


03:00.0 Network controller: Qualcomm Atheros Device 0041 (rev 20)
    Subsystem: Lenovo Device 3545
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at c1000000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: ath10k_pci
```


Sorry, it's my first days with linux!

---

### Post by praseodym on 2015-12-29
Please check key combos like Fn+F2, see the hard block at "rfkill list".

---

### Post by derpyhooves2 on 2015-12-29
It doesn't seem that Fn+F2 change something (is it possible to be so?), and there are no neither hard nor soft blocks (the print out is in the post, but I just checked once again).

---

