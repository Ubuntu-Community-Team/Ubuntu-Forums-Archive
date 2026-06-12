---
title: "Problem Wifi : Intrepid &amp; Belkin"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by wrm1862 on 2008-11-26
Hello, i've recently install Intrepid Ibex, the network-manger don't show wireless connexion.On LiveCD, he show the wireless connexion on networkmanger but i can't connect on it... ihave a Belkin F5D6050. 

(Sorry for my english.. i'm french.)

> remi@remi-desktop:~$ **cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
> remi@remi-desktop:~$ **lsusb**
Bus 002 Device 003: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 0d5c:a002 Belkin F5D6050 802.11b Adapter
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
> remi@remi-desktop:~$ **lspci**
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
04:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
> remi@remi-desktop:~$ **sudo lshw -C network**
[sudo] password for remi: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: eth0
       version: 10
       serial: 00:01:6c:0d:f7:4e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:bd:64:41:14
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=8.101.5-84 wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:cc:a4:d5:e1:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
> remi@remi-desktop:~$ **lsmod**
Module                  Size  Used by
ipv6                  263972  14 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
sbs                    19464  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
container              11520  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
pcspkr                 10624  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
i2c_viapro             15764  0 
evdev                  17696  7 
i2c_core               31892  1 i2c_viapro
at76_usb              101732  0 
button                 14224  0 
via_agp                16256  1 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  1 via_agp
ext3                  133256  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  0 
libusual               27156  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
8139cp                 27520  0 
sg                     39732  0 
pata_via               16132  0 
8139too                31616  0 
ohci1394               37936  0 
uhci_hcd               30736  0 
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
mii                    13440  2 8139cp,8139too
ata_generic            12932  0 
sata_via               15492  4 
pata_acpi              12160  0 
usbcore               148848  7 at76_usb,usb_storage,libusual,usbhid,uhci_hcd,ehci_hcd
libata                177312  4 pata_via,ata_generic,sata_via,pata_acpi
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5
> remi@remi-desktop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
> remi@remi-desktop:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:01:6c:0d:f7:4e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x9c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)
> remi@remi-desktop:~$ **sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.
> remi@remi-desktop:~$ **uname -r -m**
2.6.27-7-generic i686
> remi@remi-desktop:~$ **cat  /etc/network/interfaces**
auto lo
iface lo inet loopback
> remi@remi-desktop:~$ **nm-tool**

NetworkManager Tool

State: disconnected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:01:6C:0D:F7:4E

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Settings

Thanks

---

### Post by bedake on 2009-01-12
I believe i am experiencing this exact problem

---

### Post by wren42 on 2009-03-09
Me too? Anyone have a suggestion for what to do?

---

### Post by unrevealed01 on 2009-03-10
hi guys, 

From my experience with Ubuntu 8.10,

1)  try to find out the latest driver for your hardware.

2) blacklist the default driver that exist in kernel
 
3) Remove the default driver that exist in kernel

4) install the new driver

this might work for you.

All the best guys. notify me the progress maybe i can help you guys:P

Also refer to the manual which is given at main.
It was very helpful for me

---

