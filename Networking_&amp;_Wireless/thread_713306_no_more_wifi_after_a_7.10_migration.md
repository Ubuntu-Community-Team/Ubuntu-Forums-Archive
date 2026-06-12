---
title: "no more wifi after a 7.10 migration"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by neburzaragoza on 2008-03-02
here I copy ALL the information related to the wifi. I hope i could help:

```

rumbaruben@rumbaruben-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

rumbaruben@rumbaruben-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

rumbaruben@rumbaruben-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

rumbaruben@rumbaruben-laptop:~$ sudo lshw -C network
[sudo] password for rumbaruben:
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:38:18:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.133 latency=173 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 02
       serial: 00:16:ce:41:e5:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

rumbaruben@rumbaruben-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  273892  8 
snd_rtctimer            4384  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
ac                      6148  0 
button                  8976  0 
container               5504  0 
dock                   10656  0 
video                  18060  0 
sbs                    19592  0 
battery                11012  0 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
vfat                   14080  2 
fat                    54300  1 vfat
ndiswrapper           185240  0 
parport_pc             37412  0 
af_packet              24840  8 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17664  1 snd_pcm_oss
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
snd_seq_dummy           4740  0 
joydev                 11328  0 
ieee80211_crypt_wep     6272  1 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 41388  0 
bcm43xx               127336  0 
psmouse                39952  0 
pcspkr                  4224  0 
snd                    54660  24 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ieee80211softmac       31360  1 bcm43xx
i2c_sis96x              6404  0 
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
serio_raw               8068  0 
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
i2c_core               26112  1 i2c_sis96x
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
sis_agp                10116  1 
agpgart                35016  1 sis_agp
evdev                  11136  6 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  6 
ata_generic             8452  0 
ehci_hcd               36492  0 
sis900                 24960  0 
mii                     6528  1 sis900
ohci_hcd               22916  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,ohci_hcd
pata_sis               15236  5 
libata                125168  2 ata_generic,pata_sis
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

rumbaruben@rumbaruben-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"WLAN_D4"  Nickname:"WLAN_D4"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:60:B3:F2:65:FD   
          Bit Rate=24 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=60/100  Signal level=-54 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:54  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rumbaruben@rumbaruben-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:16:36:38:18:59  
          inet6 addr: fe80::216:36ff:fe38:1859/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:1423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1619 errors:0 dropped:2 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1110256 (1.0 MB)  TX bytes:239568 (233.9 KB)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  direcciónHW 00:16:CE:41:E5:49  
          inet6 addr: fe80::216:ceff:fe41:e549/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:203 errors:0 dropped:458 overruns:0 frame:0
          TX packets:3882 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:16849 (16.4 KB)  TX bytes:187200 (182.8 KB)
          Interrupt:3 Base address:0x8000 

eth1:avah Link encap:Ethernet  direcciónHW 00:16:CE:41:E5:49  
          inet addr:169.254.7.119  Difusión:169.254.255.255  Mask:255.255.0.0
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x8000 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:5870 (5.7 KB)  TX bytes:5870 (5.7 KB)

rumbaruben@rumbaruben-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: BA:D6:94:6B:59:A3
                    ESSID:"hpsetup"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=89/100  Signal level=-45 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 20ms ago
          Cell 02 - Address: 00:60:B3:F2:65:FD
                    ESSID:"WLAN_D4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-42 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 204ms ago
          Cell 03 - Address: 00:0D:54:A4:80:CF
                    ESSID:"3Com"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-44 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 16ms ago
          Cell 04 - Address: 00:60:B3:57:1B:12
                    ESSID:"WLAN_83"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-76 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 128ms ago
          Cell 05 - Address: 00:02:CF:5F:27:22
                    ESSID:"WLAN_C1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=60/100  Signal level=-85 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 56ms ago
          Cell 06 - Address: 00:01:38:9F:56:D9
                    ESSID:"WLAN_2A"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-79 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 756ms ago

rumbaruben@rumbaruben-laptop:~$ uname -r -m 
2.6.22-14-generic i686
rumbaruben@rumbaruben-laptop:~$ cat  /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-key s:XXXXX (necéssaire?????)
wireless-essid WLAN_D4

auto eth1

```

do you guys have any idea or suggestion??

thnx

---

### Post by kevdog on 2008-03-02
What driver were you using previously?  Im seeing a broadcom chipset.  So it was either bcm43xx or ndiswrapper.

---

### Post by neburzaragoza on 2008-03-03
I installed a lot of things, so all the names are very familiar to me. I know I installed the ndiswrapper, I think that was the driver, but I don't what i did with the bcm43xxx.

Now i'm using ndiswrapper, without any doubt.

any idea?

---

