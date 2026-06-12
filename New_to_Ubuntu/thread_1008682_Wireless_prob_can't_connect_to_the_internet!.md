---
title: "Wireless prob: can't connect to the internet!"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by FountainDew on 2008-12-11
[IMG]http://img386.imageshack.us/img386/7126/wirelessubuntuwd3.jpg[/IMG]

My problem is whats shown above, I just can't connect to my router! All my other computers are just fine but this one little stubborn laptop! The worst part is that it was **running just fine until I began installing KGET**.

Driver Installation was done like so ([[COLOR="Navy"]following these instructions[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6351422#post6351422")):
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz

tar -xvf madwifi-hal-0.10.5.6-current.tar.gz

cd madwifi-hal-0.10.5.6-r3879-20081204

sudo apt-get install build-essential linux-headers-$(uname -r)

sudo make

sudo make install
```

Background info: I have an [[COLOR="Navy"]Acer Aspire One, 1GB RAM, 8GB SSD[/COLOR]]("http://en.wikipedia.org/wiki/Aspire_One"). It original came with Linpus Lite Linux which I hastily replaced with Ubuntu 8.10 that was installed via USB Key successfully.

Help!:confused:

---

### Post by halitech on 2008-12-11
in a terminal, whats the output of ```
sudo iwconfig
```

---

### Post by Crafty Kisses on 2008-12-11
What are the results for this command?
```
lshw -C network
```
I'd also like to see the following:
```
lspci
```

---

### Post by FountainDew on 2008-12-11
[SIZE="5"]sudo iwconfig[/SIZE]
```
sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


[SIZE="5"]lspci[/SIZE]
```
lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
```


[SIZE="5"]lshw -C network[/SIZE]
```
lshw -C network

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:d8:c7:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:23:4d:03:b0:72
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:57:2d:82:6a:e8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

