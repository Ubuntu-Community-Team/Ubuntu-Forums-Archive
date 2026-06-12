---
title: "DEXP Aquilon O103 Wi-fi hard blockerd"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by bytenk on 2015-09-03
Hi all!
I'm using All-in-One PC Dexp Aquilon O103 (it's a local brand and seems to be unknown worldwire). It seems that all hardware used in my AIO PC is taken from the same named Dexp Aquilon O103 **LAPTOP**.
I believe it the case why built-in Realtek RTL8188EE Wi-Fi adapter is hard blocked under Ubuntu 14.04 LTS x32 Desktop.
The package of my AIO PC doesn't include keyboard, and there are also no hard-switch on the AIO PC. 
Here is what rfkill says:
```
guestaccess@GuestAccess-1:~$ rfkill list
0: phy0: Wireless LAN
           Soft blocked: no
           Hard blocked: yes
```
Ubuntu is installed side-by-side with "windows 7 starter" and wireless works well under windows. It's also interesting that after booting windows and then rebooting to ubuntu, wireless adapter becomes unblocked and works well... But next time, I'm booting Ubuntu I get hard block again.

Here is some additional info:
lspci
```
guestaccess@GuestAccess-1:~$ lspci -nn | grep RTL
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)

```

ifconfig
```
guestaccess@GuestAccess-1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:81:1e:4b:18  
          inet addr:192.168.111.85  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::223:81ff:fe1e:4b18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2460427 (2.4 MB)  TX bytes:536577 (536.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:36857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2601620 (2.6 MB)  TX bytes:2601620 (2.6 MB)

wlan0     Link encap:Ethernet  HWaddr 30:10:b3:69:df:7f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

rfkill
```
guestaccess@GuestAccess-1:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
guestaccess@GuestAccess-1:~$ sudo rfkill unblock all
[sudo] password for guestaccess: 
guestaccess@GuestAccess-1:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

lshw
```
guestaccess@GuestAccess-1:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: 00:23:81:1e:4b:18
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.111.85 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:89 ioport:e000(size=256) memory:d0704000-d0704fff memory:d0700000-d0703fff
  *-network DISABLED
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 30:10:b3:69:df:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.19.0-26-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:93 ioport:d000(size=256) memory:d0600000-d0603fff
```

lsmod
```
guestaccess@GuestAccess-1:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: 00:23:81:1e:4b:18
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.111.85 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:89 ioport:e000(size=256) memory:d0704000-d0704fff memory:d0700000-d0703fff
  *-network DISABLED
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 30:10:b3:69:df:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.19.0-26-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:93 ioport:d000(size=256) memory:d0600000-d0603fff
```

Could any one help me? I don't want to boot win7 each time I need wireless access to the Internet.

P.S.: [spoiler] tag, i really miss you :-(

---

### Post by bytenk on 2015-09-04
I also took some advices given by [chili555]("http://ubuntuforums.org/member.php?u=35909") in some similar threads, but it didn't work/

---

### Post by varlesh-l on 2015-10-06
I confirm this wifi hard blocked and no sound on built-in speakers. If you load to Windows and disable hibernation on regedit:
HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Control \ Power and change both *HiberFileSizePercent* and *HibernateEnabled* value data to 0
Reboot - WiFi and sound working fine on Ubuntu. But if restart/ power off PC again - wi-fi hard blocked and no sound again.
How solved this problem?
DEXP Aquilon O104

---

