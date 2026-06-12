---
title: "RTL8185 weird issue pls help"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by shvanze on 2008-10-22
If anyone could help.....
I've got RTL8185 chipset based card and I've managed to install it's Windows driver using ndiswrapper and it seems to be working.
Network Manager found my network but couldn't connect and after rebeoot it didn't find any networks anymore so I've installed WICD.
WICD also can't find any networks...

ndiswrapper -v:
> utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-21-generic/misc/ndiswrapper.ko
version:        1.53
vermagic:       2.6.24-21-generic SMP mod_unload 586

ndiswrapper -l:
> net8185 : driver installed
	device (10EC:8185) present

lspci -nn:
> 00:00.0 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:0282]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:1282]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:2282]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:3282]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:4282]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:7282]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:09.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:09.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:09.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
00:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
00:0e.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)

lshw -C Network:
>   *-network:0             
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wlan0
       version: 20
       serial: 00:1d:0f:b6:9a:4d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.53+TP-LINK TECHNOLOGIES CO., L latency=32 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 11
       serial: 00:50:8d:7d:e5:84
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.14 duplex=full ip=192.168.0.100 latency=32 link=yes maxlatency=8 mingnt=3 module=via_velocity multicast=yes port=twisted pair speed=100MB/s

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod:
> Module                  Size  Used by
ipv6                  267780  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
af_packet              23812  4 
ac                      6916  0 
ndiswrapper           193436  0 
lp                     12324  0 
snd_usb_audio          83936  0 
snd_usb_lib            18432  1 snd_usb_audio
snd_hwdep              10500  1 snd_usb_audio
hci_usb                16540  2 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
evdev                  13056  3 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
nvidia               7825536  24 
snd_via82xx            29464  1 
gameport               16008  1 snd_via82xx
snd_ac97_codec        101028  1 snd_via82xx
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_usb_audio,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9728  1 snd_via82xx
snd_seq_dummy           4868  0 
pcspkr                  4224  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
button                  9232  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                  6656  0 
i2c_viapro              9876  0 
snd                    56996  17 snd_usb_audio,snd_usb_lib,snd_hwdep,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               24832  2 nvidia,i2c_viapro
amd64_agp              13444  1 
soundcore               8800  1 snd
agpgart                34760  2 nvidia,amd64_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 32128  0 
hid                    38784  1 usbhid
pata_via               13316  2 
ata_generic             8324  0 
floppy                 59588  0 
sata_via               12420  0 
pata_acpi               8320  0 
uhci_hcd               27024  0 
libata                159344  4 pata_via,ata_generic,sata_via,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
via_velocity           32772  0 
crc_ccitt               3072  1 via_velocity
ehci_hcd               37900  0 
ohci_hcd               26640  0 
usbcore               146412  9 ndiswrapper,snd_usb_audio,snd_usb_lib,hci_usb,usbhid,uhci_hcd,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

/etc/modprobe.d/blacklist:
> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist rtl818x
blacklist rtl8187
blacklist rtl8185
blacklist r8185
blacklist bcm43xx
blacklist b43
blacklist rt2500

/etc/network/interfaces:
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

/etc/modules:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

ndiswrapper

ndiswrapper has been modprobe'd
```

modprobe ndiswrapper
```


Anyone help please.

---

