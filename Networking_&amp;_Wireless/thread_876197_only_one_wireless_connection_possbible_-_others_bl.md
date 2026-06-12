---
title: "only one wireless connection possbible - others blocked"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by neburzaragoza on 2008-07-31
Hi there,

I can't connect with my wireless to any net, but one, the one from my neighbor. I have my own wifi at home but even with the cable it is imposible to success the connection. i feel like it is blocked.

Below I let you know the response of some commands that could be helpful to understand what happening.

```

~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:38:18:59
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half ip=212.97.173.81 latency=173 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:41:e5:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.107 multicast=yes wireless=IEEE 802.11g

~$ lsmod
Module                  Size  Used by
af_packet              23812  6 
ipv6                  267780  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5504  0 
ppdev                  10372  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
evdev                  13056  7 
b43                   144420  0 
snd_seq_dummy           4868  0 
wmi_acer                9644  0 
serio_raw               7940  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
psmouse                40336  0 
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
battery                14212  0 
ac                      6916  0 
button                  9232  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcspkr                  4224  0 
soundcore               8800  1 snd
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
sis_agp                10116  1 
i2c_sis96x              6148  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  1 sis_agp
i2c_core               24832  1 i2c_sis96x
ext3                  136712  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  6 
ata_generic             8324  0 
pata_acpi               8320  0 
ehci_hcd               37900  0 
ssb                    34308  1 b43
ohci_hcd               25348  0 
pata_sis               15236  5 
sis900                 24320  0 
mii                     6400  1 sis900
usbcore               146028  3 ehci_hcd,ohci_hcd
libata                159344  3 ata_generic,pata_acpi,pata_sis
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:2E:4C:56   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=53/100  Signal level=-62 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:16:36:38:18:59  
          inet dirección:212.97.173.81  Difusión:255.255.255.255  Máscara:255.255.248.0
          dirección inet6: fe80::216:36ff:fe38:1859/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:1 overruns:0 carrier:0
          colisiones:1 txqueuelen:1000 
          RX bytes:110852 (108.2 KB)  TX bytes:29742 (29.0 KB)
          Interrupción:16 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1002 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:52876 (51.6 KB)  TX bytes:52876 (51.6 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:16:ce:41:e5:49  
          inet dirección:192.168.1.107  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::216:ceff:fe41:e549/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1492  Métrica:1
          RX packets:1429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:966 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:919280 (897.7 KB)  TX bytes:181270 (177.0 KB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-16-CE-41-E5-49-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:2E:4C:56
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/100  Signal level=-64 dBm  Noise level=-73 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002aa833c4a7

~$ uname -r -m 
2.6.24-19-generic i686

~$ cat  /etc/network/interfaces
auto lo
iface lo inet loopback



```

any idea or suggestion will be appreciated.

thanks in advance

---

