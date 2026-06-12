---
title: "impossible to get an ip address from dhcp"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by martine.ginette on 2008-06-03
Hello,

I have just arrived in California (from France), and the only problem I have to face -everything is so perfect around here!- is that my MacBook only get an ip address when I use MacOS, whereas I really do not like MacOS and I really prefer my KUBUNTU.

Here are some informations about my computer:

```

genet@genet:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

```

```

genet@genet:~$ lsusb
Bus 005 Device 011: ID 05ac:8300 Apple Computer, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 006: ID 05ac:1000 Apple Computer, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 005: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 008: ID 05ac:0218 Apple Computer, Inc.
Bus 001 Device 001: ID 0000:0000

```

```

genet@genet:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Contro                                     ller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated G                                     raphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Grap                                     hics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (                                     rev 22)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter                                      (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

```

genet@genet:~$ sudo lshw -C network
[sudo] password for genet:
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:30:2d:c4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=128.111.164.26 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:f2:51:c2:db
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

```

genet@genet:~$ lsmod
Module                  Size  Used by
ath_pci               101024  0
sky2                   47492  0
wlan_wep                8064  0
af_packet              23812  2
hci_usb                16540  0
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  5 hci_usb,rfcomm,l2cap
ppdev                  10372  0
ipv6                  267780  12
acpi_cpufreq           10796  1
cpufreq_stats           7104  0
cpufreq_conservative     8712  0
cpufreq_powersave       2688  2
cpufreq_ondemand        9740  0
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0
sbs                    15112  0
sbshc                   7680  1 sbs
container               5632  0
dock                   11280  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_utf8                2944  1
hfsplus                79748  1
nls_iso8859_1           4992  1
nls_cp437               6656  1
vfat                   14464  1
fat                    54556  1 vfat
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
applesmc               21164  0
led_class               6020  1 applesmc
input_polldev           5896  1 applesmc
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0
appleir                 7040  0
snd_hda_intel         344728  1
snd_pcm_oss            42144  0
wlan_scan_sta          14720  1
snd_mixer_oss          17920  1 snd_pcm_oss
uvcvideo               58116  0
ath_rate_sample        14336  1
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
usbhid                 31872  0
hid                    38784  1 usbhid
appletouch             11264  0
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
wlan                  207728  5 ath_pci,wlan_wep,wlan_scan_sta,ath_rate_sample
ath_hal               192592  3 ath_pci,ath_rate_sample
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  0
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
battery                14212  0
button                  9232  0
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  1
agpgart                34760  2 intel_agp
tpm_infineon           10152  0
tpm                    16544  1 tpm_infineon
tpm_bios                8320  1 tpm
pcspkr                  4224  0
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
evdev                  13056  9
ext3                  136712  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
sd_mod                 30720  5
pata_acpi               8320  0
ata_piix               19588  4
ata_generic             8324  0
ehci_hcd               37900  0
libata                159344  3 pata_acpi,ata_piix,ata_generic
uhci_hcd               27024  0
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0
ieee1394               93752  2 sbp2,ohci1394
usbcore               146028  8 hci_usb,appleir,uvcvideo,usbhid,appletouch,ehci_hcd,uhci_hcd
thermal                16796  0
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

```

```

genet@genet:~$ uname -r -m
2.6.24-16-generic i686

```

And this is me trying to connect:

```

genet@genet:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:17:f2:51:c2:db
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:0 (0.0 B) Octets transmis:5734 (5.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:17:f2:30:2d:c4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17

lo        Link encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:24 erreurs:0 :0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:2092 (2.0 KB) Octets transmis:2092 (2.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-17-F2-51-C2-DB-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:11613 erreurs:0 :0 overruns:0 frame:18126
          TX packets:869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:199
          Octets reçus:990609 (967.3 KB) Octets transmis:45650 (44.5 KB)
          Interruption:16

```

```

genet@genet:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-88 dBm  Noise level=-88 dBm
          Rx invalid nwid:10145  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

genet@genet:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:6C:46:60:32
                    ESSID:"batcave II"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-45 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

```

```

genet@genet:~$ sudo iwconfig ath0 essid "batcave II"

```

```

genet@genet:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"batcave II"  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:10867  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

genet@genet:~$ sudo iwconfig ath0 key **********

```

```

genet@genet:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 7160
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:51:c2:db
Sending on   LPF/ath0/00:17:f2:51:c2:db
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

If somebody has an idea on how I can get an IP address, I would be please to hear it!

Thanks so much!

Martin.

---

### Post by vexingmodstwo on 2008-06-03
> **martin.genet said:**
> Hello,

I have just arrived in California (from France), and the only problem I have to face -everything is so perfect around here!- is that my MacBook only get an ip address when I use MacOS, whereas I really do not like MacOS and I really prefer my KUBUNTU.

Here are some informations about my computer:

```

genet@genet:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

```

```

genet@genet:~$ lsusb
Bus 005 Device 011: ID 05ac:8300 Apple Computer, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 006: ID 05ac:1000 Apple Computer, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 005: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 008: ID 05ac:0218 Apple Computer, Inc.
Bus 001 Device 001: ID 0000:0000

```

```

genet@genet:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Contro                                     ller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated G                                     raphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Grap                                     hics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (                                     rev 22)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter                                      (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

```

genet@genet:~$ sudo lshw -C network
[sudo] password for genet:
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:30:2d:c4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=128.111.164.26 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:f2:51:c2:db
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

```

genet@genet:~$ lsmod
Module                  Size  Used by
ath_pci               101024  0
sky2                   47492  0
wlan_wep                8064  0
af_packet              23812  2
hci_usb                16540  0
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  5 hci_usb,rfcomm,l2cap
ppdev                  10372  0
ipv6                  267780  12
acpi_cpufreq           10796  1
cpufreq_stats           7104  0
cpufreq_conservative     8712  0
cpufreq_powersave       2688  2
cpufreq_ondemand        9740  0
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0
sbs                    15112  0
sbshc                   7680  1 sbs
container               5632  0
dock                   11280  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_utf8                2944  1
hfsplus                79748  1
nls_iso8859_1           4992  1
nls_cp437               6656  1
vfat                   14464  1
fat                    54556  1 vfat
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
applesmc               21164  0
led_class               6020  1 applesmc
input_polldev           5896  1 applesmc
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0
appleir                 7040  0
snd_hda_intel         344728  1
snd_pcm_oss            42144  0
wlan_scan_sta          14720  1
snd_mixer_oss          17920  1 snd_pcm_oss
uvcvideo               58116  0
ath_rate_sample        14336  1
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
usbhid                 31872  0
hid                    38784  1 usbhid
appletouch             11264  0
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
wlan                  207728  5 ath_pci,wlan_wep,wlan_scan_sta,ath_rate_sample
ath_hal               192592  3 ath_pci,ath_rate_sample
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  0
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
battery                14212  0
button                  9232  0
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  1
agpgart                34760  2 intel_agp
tpm_infineon           10152  0
tpm                    16544  1 tpm_infineon
tpm_bios                8320  1 tpm
pcspkr                  4224  0
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
evdev                  13056  9
ext3                  136712  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
sd_mod                 30720  5
pata_acpi               8320  0
ata_piix               19588  4
ata_generic             8324  0
ehci_hcd               37900  0
libata                159344  3 pata_acpi,ata_piix,ata_generic
uhci_hcd               27024  0
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0
ieee1394               93752  2 sbp2,ohci1394
usbcore               146028  8 hci_usb,appleir,uvcvideo,usbhid,appletouch,ehci_hcd,uhci_hcd
thermal                16796  0
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

```

```

genet@genet:~$ uname -r -m
2.6.24-16-generic i686

```

And this is me trying to connect:

```

genet@genet:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:17:f2:51:c2:db
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:0 (0.0 B) Octets transmis:5734 (5.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:17:f2:30:2d:c4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17

lo        Link encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:24 erreurs:0 :0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:2092 (2.0 KB) Octets transmis:2092 (2.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-17-F2-51-C2-DB-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:11613 erreurs:0 :0 overruns:0 frame:18126
          TX packets:869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:199
          Octets reçus:990609 (967.3 KB) Octets transmis:45650 (44.5 KB)
          Interruption:16

```

```

genet@genet:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-88 dBm  Noise level=-88 dBm
          Rx invalid nwid:10145  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

genet@genet:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:6C:46:60:32
                    ESSID:"batcave II"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-45 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

```

```

genet@genet:~$ sudo iwconfig ath0 essid "batcave II"

```

```

genet@genet:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"batcave II"  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:10867  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

genet@genet:~$ sudo iwconfig ath0 key **********

```

```

genet@genet:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 7160
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:51:c2:db
Sending on   LPF/ath0/00:17:f2:51:c2:db
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

If somebody has an idea on how I can get an IP address, I would be please to hear it!

Thanks so much!

Martin.

Try to manually configure the connection through the network manager using the same IP address the router uses for when you're in "mac mode".  Make sure to input the default gateway address too.

I don't know why but that worked for me.  I think there's something wrong with how certain setups handle the DHCP stuff.

---

### Post by martine.ginette on 2008-06-04
I face an interesting behavior...

I tried what you said but it did not work.

Then, I went back on OSX, tried to connect with a specified IP address, it did not work. Then, back on KUBUNTU, I tried to connect with DHCP, it worked! Then, I tried to disconnect and connect again with DHCP, it did not work...

The interesting point is that when I do it again (OSX, fixed IP address try, KUBUNTU, DHCP), it works...

Do you have an idea?

---

### Post by bla on 2008-06-04
I have a very similar problem... no help yet.
It seems like an ubuntu/kubuntu issue.

[http://ubuntuforums.org/showthread.php?t=813225](http://ubuntuforums.org/showthread.php?t=813225)

---

