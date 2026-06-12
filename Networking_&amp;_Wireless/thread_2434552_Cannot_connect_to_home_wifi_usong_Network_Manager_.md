---
title: "Cannot connect to home wifi usong Network Manager (Atheros AR9485)"
date: 2020-01-07
forum: Networking &amp; Wireless
---

### Post by d3ntin on 2020-01-07
I have acquired a laptop, an Asus Vivobook S310L, and I got Kubuntu  19.04 installed. It runs like a charm, but I have an issue with my wifi.  It is simply unable to connect to my home wireless...Network manager  tries to connect, but hangs when getting the address and then gives up  and disconnects the network. But it can connect to the hotspot I create  with my smartphone (I tried with 2 different smartphones). The laptop is  equipped with an Atheros AR9485 chipset. It showed also low signal  issues, which I resolved disabling the bluetooth from the BIOS. But it  could never connect to my wifi. 
  The strangest thing is that, under the same conditions (same place on  the same desk, same Kubuntu version, Network manager version) my  desktop has no problems with my wifi. The only difference is that it has  a USB dongle with a Realtek chipset which has absolutely no flaws on  Kubuntu.
  Here some informations:

  ```

lspci

```
```

  00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Haswell-ULT Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Thermal (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars LE [Radeon HD 8530M / R5 M240]

```
```

  iwconfig

```
```

  wlp3s0    IEEE 802.11  ESSID:"D3ntin"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: A4:50:46:7E:DB:C7   
          Bit Rate=14.4 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:182   Missed beacon:0

enp2s0    no wireless extensions.

lo        no wireless extensions.

```
```

  rfkill list all

```
```

  0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```
```

  lshw -c net

```
```

         description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       serial: 24:0a:64:b2:14:e3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=5.0.0-38-generic firmware=N/A ip=192.168.43.88 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff

```

  [Here]("https://paste.ubuntu.com/p/VdrfTwFm5W/") the output of 
```
journalctl -u NetworkManager
```
  I did a fresh boot, and when KDE loaded, I tried to connect to my wifi - and, abviously, it failed.

---

### Post by chili555 on 2020-01-07
Please see my comment here: [https://askubuntu.com/questions/1201318/network-manager-cant-get-ip-on-home-wifi-atheros-ar9485](https://askubuntu.com/questions/1201318/network-manager-cant-get-ip-on-home-wifi-atheros-ar9485)

---

### Post by d3ntin on 2020-01-28
It was exactly what chili555 said: one of the two antennas disconnected. Now it works like a charm, even with bluetooth enabled...thanks (again :D)!

---

