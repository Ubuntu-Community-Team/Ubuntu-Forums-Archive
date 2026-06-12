---
title: "Troubleshooting wired ethernet connection"
date: 2014-01-04
forum: Networking &amp; Wireless
---

### Post by timmytimmytimmy7 on 2014-01-04
I recently installed Lubuntu 12.10, and cannot connect to the internet via a wired ethernet connection (or a wireless connection for that matter). I read many theads on these forums, but was unable to solve my problem (admittedly, this is probably because I didn't really understand most of the solutions, and was just blindly trying to copy solutions). Anyway, here are the outputs of some of the commands people used to diagnose the problem in other threads -- any help would be greatly appreciated.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:03:25:3e:2f:20  
          inet addr:10.12.136.15  Bcast:10.12.137.255  Mask:255.255.254.0
          inet6 addr: fe80::203:25ff:fe3e:2f20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1134143 (1.1 MB)  TX bytes:23688 (23.6 KB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102403 (102.4 KB)  TX bytes:102403 (102.4 KB)
```

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
01:00.0 PCI bridge: NVIDIA Corporation Device 01b3 (rev a3)
02:00.0 PCI bridge: NVIDIA Corporation Device 01b3 (rev a3)
02:01.0 PCI bridge: NVIDIA Corporation Device 01b3 (rev a3)
03:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8700M GT] (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0a:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
0b:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0b:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0b:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
```

lsmod:
```
Module                  Size  Used by
vesafb                 13477  1 
joydev                 17161  0 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
arc4                   12473  2 
gpio_ich               13159  0 
snd_hda_codec_realtek    63356  1 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  12 
bnep                   17707  2 
snd_hda_intel          32515  1 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
microcode              18209  0 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                84843  0 
cx23885               141056  0 
rc_core                21266  1 cx23885
videobuf_dma_sg        18714  1 cx23885
altera_stapl           30193  1 cx23885
snd_pcm                80163  3 snd_hda_intel,snd_hda_codec,cx23885
cx2341x                27699  1 cx23885
tda18271               40771  1 cx23885
gspca_m5602            51266  0 
gspca_main             27626  1 gspca_m5602
nouveau               823577  0 
iwl4965               106888  0 
ttm                    75534  1 nouveau
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         45271  1 nouveau
drm                   230463  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
btusb                  17950  0 
video                  18847  1 nouveau
serio_raw              13031  0 
wmi                    18590  2 nouveau,mxm_wmi
iwlegacy               87736  1 iwl4965
mac80211              461161  2 iwl4965,iwlegacy
bluetooth             183228  22 rfcomm,bnep,btusb
r592                   17707  0 
cfg80211              175375  3 iwl4965,iwlegacy,mac80211
memstick               15842  1 r592
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                16925  0 
mac_hid                13037  0 
snd                    61991  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,cx23885,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
soundcore              14599  1 snd
videobuf_dvb           13820  1 cx23885
videobuf_core          25097  3 cx23885,videobuf_dma_sg,videobuf_dvb
v4l2_common            15767  2 cx23885,cx2341x
videodev               95841  4 cx23885,cx2341x,gspca_main,v4l2_common
altera_ci              19022  1 cx23885
dvb_core               98654  3 cx23885,videobuf_dvb,altera_ci
btcx_risc              13400  1 cx23885
tveeprom               17009  1 cx23885
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
sky2                   52926  0 
```

lsusb:
```
Bus 001 Device 003: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

sudo lswh -C network
```
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 00:03:25:3e:2f:20
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=10.12.136.15 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:45 memory:fbefc000-fbefffff ioport:e800(size=256) memory:fbec0000-fbedffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:21:5c:3a:f4:db
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.5.0-17-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:fbffe000-fbffffff

```

---

### Post by praseodym on 2014-01-05
Hi,

please show
```
rfkill list
cat /etc/resolv.conf
route -n
```
Please note that 12.10 is only supported until April 2014, 13.04 until January 2014 and 13.10 until July 2014. In April 2014 the next Long Term Support version 14.04 will be released, which also covers Lubuntu as LTS-version. So I recommend updating to 13.10/installing 13.10 to be prepared for Lubuntu 14.04 LTS

---

### Post by timmytimmytimmy7 on 2014-01-05
I just spent a few hours trying to get 13.10 installed, but kept getting stuck on a black screen with a cursor. I tried a number of solutions on various forums, but none of them worked, so I think that for now I'll just try to get the ethernet working under 12.10. Here are the outputs of the commands you suggested -- thanks again for your help!

rfkill list
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

cat /etc/resolv/conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search Stanford.EDU
```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.12.136.1     0.0.0.0         UG    0      0        0 eth0
10.12.136.0     0.0.0.0         255.255.254.0   U     1      0        0 eth0
```

---

### Post by Iowan on 2014-01-05
Can you ping the router/gateway?
```
ping -c3 10.12.136.1
```

---

### Post by timmytimmytimmy7 on 2014-01-05
ping -c3 10.12.136.1
```
PING 10.12.136.1 (10.12.136.1) 56(84) bytes of data.
From 10.12.136.15 icmp_seq=1 Destination Host Unreachable
From 10.12.136.15 icmp_seq=2 Destination Host Unreachable
From 10.12.136.15 icmp_seq=3 Destination Host Unreachable

--- 10.12.136.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2007ms
pipe 2
```

---

