---
title: "Wireless networks not found/can't connect"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by tpv616 on 2008-05-09
Hi,
I recently got a Toshiba Satellite A215-S5837 laptop, and I just installed Ubuntu 8.04 Hardy Heron on it (dual-boot with Vista). Apparently, my wireless card is an Atheros AR5007EG (according to Vista's dev mgr.), and I heard the restricted drivers don't work, so I followed ToM-X's instructions in the 7th post in this thread:

[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

I installed Madwifi and the interface shows up:
```

tpv@tpv-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:07:4d:32
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.9 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:8f:f6:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

I also ran iwconfig:

```

tpv@tpv-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tpv@tpv-laptop:~$ 

```
I am confused, though, because there are two interfaces: ath0 and wifi0.

Also, I tried to connect through GNOME's network manager, but my wireless network didn't appear at all. I tried to enter it in manually, but it wouldn't connect. Any help would be great.

(By the way, I only disabled the HAL driver in the hardware driver manager, not the support driver. Maybe that has something to do with it... but I don't know.)

---

### Post by tpv616 on 2008-05-09
D'oh. I forgot I had turned off the wireless adapter in Windows. It works now :)

---

