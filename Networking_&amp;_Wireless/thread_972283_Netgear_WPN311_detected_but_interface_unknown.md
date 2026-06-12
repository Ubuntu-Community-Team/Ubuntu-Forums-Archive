---
title: "Netgear WPN311 detected but interface unknown"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by Flavien on 2008-11-05
Hello everybody,

I just finished to install Ubuntu server 8.10 but I have some problems successfully configuring my Wifi card: Netgear WPN311.
I have spent two days trying to configure it without success. Even in the forums I did not find anything really relevant, that's why I come here to ask you some help.

As you already know now, my WiFi card is a Netgear WPN311 (chipset atheros according to this [page](http://doc.ubuntu-fr.org/wifi_liste_carte#n)) and seems to be well detected.

I guess that my /etc/network/interfaces file is well structures, but here's the main problem:

sudo ifup wlan0```
Ignoring unknown interface wlan0=wlan0.
```
I really don't understand why this error occurs.

Here are useful informations:

sudo cat /etc/lsb-release```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```
sudo lsusb
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
sudo lspci```
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
07:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
07:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
```
sudo lshw -C network
```
  *-network:0 DISABLED
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wmaster0
       version: 00
       serial: 00:1c:10:e4:be:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface

       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth0
       version: 10
       serial: 00:40:f4:8e:6b:cf
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
```
sudo lsmod
```
Module                  Size  Used by
ipv6                  263460  16
af_packet              25600  2
iptable_filter         10752  0
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29708  0
lp                     17156  0
loop                   23180  0
tda1004x               24324  1
saa7134_dvb            27532  0
arc4                    9984  2
ecb                    10880  2
crypto_blkcipher       25348  1 ecb
videobuf_dvb           12932  1 saa7134_dvb
dvb_core               86016  2 saa7134_dvb,videobuf_dvb
tda827x                17796  2
tda8290                20868  1
tuner                  33096  0
rt61pci                27776  0
crc_itu_t              10112  1 rt61pci
rt2x00pci              15232  1 rt61pci
rt2x00lib              36224  2 rt61pci,rt2x00pci
serio_raw              13444  0
evdev                  17696  0
rfkill                 17048  1 rt2x00lib
saa7134               147028  1 saa7134_dvb
led_class              12164  1 rt2x00lib
psmouse                45200  0
snd_hda_intel         381360  0
ir_common              48132  1 saa7134
mac80211              216692  2 rt2x00pci,rt2x00lib
snd_pcm                83332  1 snd_hda_intel
k8temp                 12416  0
videodev               41344  2 tuner,saa7134
v4l1_compat            22404  1 videodev
compat_ioctl32          9344  1 saa7134
snd_timer              29832  1 snd_pcm
snd                    63268  3 snd_hda_intel,snd_pcm,snd_timer
v4l2_common            19840  2 tuner,saa7134
videobuf_dma_sg        20612  2 saa7134_dvb,saa7134
videobuf_core          26628  3 videobuf_dvb,saa7134,videobuf_dma_sg
soundcore              15328  1 snd
shpchp                 38036  0
pci_hotplug            35236  1 shpchp
tveeprom               20228  1 saa7134
snd_page_alloc         16264  2 snd_hda_intel,snd_pcm
cfg80211               32392  2 rt2x00lib,mac80211
eeprom_93cx6           10240  1 rt61pci
parport_pc             39460  1
parport                42604  2 lp,parport_pc
cfi_cmdset_0002        30720  1
cfi_util               11392  1 cfi_cmdset_0002
jedec_probe            19968  0
cfi_probe              13568  0
button                 14224  0
gen_probe              11264  2 jedec_probe,cfi_probe
ck804xrom              13060  0
mtd                    23560  3 cfi_cmdset_0002,ck804xrom
chipreg                11012  3 jedec_probe,cfi_probe,ck804xrom
i2c_nforce2            14596  0
map_funcs               9984  1 ck804xrom
i2c_core               31892  9 tda1004x,saa7134_dvb,tda827x,tda8290,tuner,saa7134,v4l2_common,tveeprom,i2c_nforce2
ext3                  132872  2
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0
cdrom                  43040  1 sr_mod
sd_mod                 42264  4
crc_t10dif              9984  1 sd_mod
sata_nv                30472  3
sg                     39220  0
pata_amd               18436  0
ata_generic            12804  0
pata_jmicron           11136  0
8139cp                 27904  0
ahci                   37004  0
ohci1394               38192  0
ieee1394               96452  2 sbp2,ohci1394
8139too                31744  0
mii                    13440  2 8139cp,8139too
pata_acpi              12160  0
forcedeth              61968  0
libata                176032  6 sata_nv,pata_amd,ata_generic,pata_jmicron,ahci,pata_acpi
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43916  0

ohci_hcd               32144  0
usbcore               149360  3 ehci_hcd,ohci_hcd
thermal                23708  0
processor              42284  1 thermal
fan                    12420  0
fbcon                  47392  0
tileblit               10752  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60700  1
```
sudo iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth2      no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
sudo ifconfig
```
eth1      Link encap:Ethernet  HWaddr 00:18:f3:99:49:56
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:2e3e:5090:218:f3ff:fe99:4956/64 Scope:Global
          inet6 addr: fe80::218:f3ff:fe99:4956/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31538283 (31.5 MB)  TX bytes:1590769 (1.5 MB)
          Interrupt:217 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```
sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```
sudo uname -r -m
```
2.6.27-7-server i686
```
sudo cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

# Wifi
auto wlan0
iface wlan inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.254
wpa-ssid vinaigre
wpa-psk ***************************************
```
I don't know if it's good to do that but I installed network-manager to run this shell command:

sudo nm-tool
```
NetworkManager Tool

State: unknown

NetworkManager appears not to be running (could not get its state).
```
Can anybody help me with this issue?

Thanks a lot for your help.

Regards,
Flavien

---

### Post by Flavien on 2008-11-06
Hi everybody,

Nobody has even a little hint?
It would be great to have just a beginning of solution as I am quite lost today.

Regards,
Flavien

---

### Post by james.king@4act.com on 2008-11-17
lol

guess I should have researched before buying my card. I have read that it works in Hardy and read an article where someone got it working in Intrepid, but they were having different troubles.

Let me know if you figure it out.

---

