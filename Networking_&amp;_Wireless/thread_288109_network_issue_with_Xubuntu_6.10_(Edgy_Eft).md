---
title: "network issue with Xubuntu 6.10 (Edgy Eft)"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by kanchata on 2006-10-29
I´re little confused with network configuration on Xubuntu Edgy Eft
the hardware are installed and work with modules loaded without error rt2x00-seialmonkey testing drivers for Ralink chipset rt61pci and companion, 80211, rate_control, etc., but the network wireless no go up, I´still are problems with DCHPCD ór client, have checked all network utils > System >>>>, terminal >>ifconfig, iwconfig, my wireless card have association with the point access and internet is unreachable, d´nt resolv addresses, are very confused about question, recent commentary for friend do Xubuntu is flawlessly distro to work with desktop take to download the iso and install then, now writing from windows, xubuntu to me are incapable to reach internet at the moment, have a litle guidelines to solve ?,
have a Slackware Distro (Vector Linux SOHO 5) installed and working  a around alls, linux experience checking with diferents system-distros, and take more 3 hours afther install system to make a internet connection and have d´nt.
Thank´s for people.

---

### Post by kanchata on 2006-10-29
> **kanchata said:**
> I´re little confused with network configuration on Xubuntu Edgy Eft
the hardware are installed and work with modules loaded without error rt2x00-seialmonkey testing drivers for Ralink chipset rt61pci and companion, 80211, rate_control, etc., but the network wireless no go up, I´still are problems with DCHPCD ór client, have checked all network utils > System >>>>, terminal >>ifconfig, iwconfig, my wireless card have association with the point access and internet is unreachable, d´nt resolv addresses, are very confused about question, recent commentary for friend do Xubuntu is flawlessly distro to work with desktop take to download the iso and install then, now writing from windows, xubuntu to me are incapable to reach internet at the moment, have a litle guidelines to solve ?,
have a Slackware Distro (Vector Linux SOHO 5) installed and working  a around alls, linux experience checking with diferents system-distros, and take more 3 hours afther install system to make a internet connection and have d´nt.
Thank´s for people.

To an curiositye´s ::::> Logiiiist
dmesg>>>
[17179602.080000] Loading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17179602.088000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[17179602.228000] wmaster0: Selected rate control algorithm 'simple'
debug>>>
:50 hot1 kernel: [17180436.576000] wlan0: no IPv6 routers present
Oct 29 11:55:11 hot1 kernel: [17180577.832000] wlan0: no IPv6 routers present
Oct 29 12:01:51 hot1 kernel: [17179569.184000] On node 0 totalpages: 98288
debug>>>
:51 hot1 kernel: [17179581.952000] PCI: setting IRQ 12 as level-triggered
Oct 29 12:01:51 hot1 kernel: [17179598.116000] wmaster0: Selected rate control algorithm 'simple'
Oct 29 12:02:08 hot1 kernel: [17179646.600000] wlan0: no IPv6 routers present
Oct 29 12:07:56 hot1 kernel: [17179994.432000] wlan0: Initial auth_alg=0
Oct 29 12:07:56 hot1 kernel: [17179994.432000] wlan0: authenticate with AP 00:a0:c5:ed:b9:9c
Oct 29 12:07:56 hot1 kernel: [17179994.436000] wlan0: RX authentication from 00:a0:c5:ed:b9:9c (alg=0 transaction=2 status=0)
Oct 29 12:07:56 hot1 kernel: [17179994.436000] wlan0: authenticated
Oct 29 12:07:56 hot1 kernel: [17179994.436000] wlan0: associate with AP 00:a0:c5:ed:b9:9c
Oct 29 12:07:56 hot1 kernel: [17179994.440000] wlan0: invalid aid value 1; bits 15:14 not set
Oct 29 12:07:56 hot1 kernel: [17179994.440000] wlan0: RX AssocResp from 00:a0:c5:ed:b9:9c (capab=0x1 status=0 aid=1)
Oct 29 12:07:56 hot1 kernel: [17179994.440000] wlan0: associated
Oct 29 12:08:06 hot1 kernel: [17180004.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:08:38 hot1 kernel: [17180036.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:09:10 hot1 kernel: [17180068.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:09:42 hot1 kernel: [17180100.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:10:14 hot1 kernel: [17180132.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:10:46 hot1 kernel: [17180164.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:11:18 hot1 kernel: [17180196.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:11:50 hot1 kernel: [17180228.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:12:22 hot1 kernel: [17180260.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:12:54 hot1 kernel: [17180292.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:13:26 hot1 kernel: [17180324.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:13:58 hot1 kernel: [17180356.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:14:30 hot1 kernel: [17180388.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:15:02 hot1 kernel: [17180420.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:15:34 hot1 kernel: [17180452.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:16:06 hot1 kernel: [17180484.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:16:50 hot1 kernel: [17180528.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:17:22 hot1 kernel: [17180560.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:17:54 hot1 kernel: [17180592.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:18:32 hot1 kernel: [17180630.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:19:04 hot1 kernel: [17180662.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:19:36 hot1 kernel: [17180694.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:20:12 hot1 kernel: [17180730.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:20:44 hot1 kernel: [17180762.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:21:16 hot1 kernel: [17180794.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:21:48 hot1 kernel: [17180826.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:22:20 hot1 kernel: [17180858.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:22:52 hot1 kernel: [17180890.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:23:24 hot1 kernel: [17180922.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:23:56 hot1 kernel: [17180954.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:24:28 hot1 kernel: [17180986.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:25:00 hot1 kernel: [17181018.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:25:32 hot1 kernel: [17181050.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:26:04 hot1 kernel: [17181082.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:26:36 hot1 kernel: [17181114.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:27:08 hot1 kernel: [17181146.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:27:40 hot1 kernel: [17181178.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:28:12 hot1 kernel: [17181210.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:28:44 hot1 kernel: [17181242.440000] wlan0: No ProbeResp from current AP 00:a0:c5:ed:b9:9c - assume out of range
Oct 29 12:36:49 hot1 kernel: [17179569.184000] On node 0 totalpages: 98288
debug>>>
Oct 29 13:38:35 hot1 kernel: [17179580.784000] PCI: setting IRQ 12 as level-triggered
Oct 29 13:38:35 hot1 kernel: [17179597.380000] wmaster0: Selected rate control algorithm 'simple'
Oct 29 13:39:28 hot1 kernel: [17179685.384000] ieee80211_crypt: registered algorithm 'NULL'
Oct 29 13:39:38 hot1 kernel: [17179695.584000] wlan0: no IPv6 routers present
Oct 29 13:43:46 hot1 kernel: [17179942.952000] wlan0: Initial auth_alg=0
Oct 29 13:43:46 hot1 kernel: [17179942.952000] wlan0: authenticate with AP 00:a0:c5:ed:b9:9c
Oct 29 13:43:46 hot1 kernel: [17179943.152000] wlan0: authenticate with AP 00:a0:c5:ed:b9:9c
Oct 29 13:43:46 hot1 kernel: [17179943.352000] wlan0: authenticate with AP 00:a0:c5:ed:b9:9c
Oct 29 13:43:46 hot1 kernel: [17179943.552000] wlan0: authentication with AP 00:a0:c5:ed:b9:9c timed out
Oct 29 14:03:04 hot1 kernel: [17181101.356000] wmaster0: Selected rate control algorithm 'simple'
Oct 29 14:03:15 hot1 kernel: [17181111.924000] wlan0: no IPv6 routers present
Oct 29 14:03:28 hot1 kernel: [17181125.140000] wlan0: no IPv6 routers present
Oct 29 14:09:54 hot1 kernel: [17181510.980000] wlan0: no IPv6 routers present
Oct 29 14:12:41 hot1 kernel: [17181677.968000] wlan0: no IPv6 routers present
Oct 29 20:58:10 hot1 kernel: [17179569.184000] On node 0 totalpages: 98288
debug>>>
Oct 29 20:58:10 hot1 kernel: [17179583.936000] PCI: setting IRQ 12 as level-triggered
Oct 29 20:58:10 hot1 kernel: [17179602.228000] wmaster0: Selected rate control algorithm 'simple'
Oct 29 20:58:10 hot1 kernel: [17179606.972000] ieee80211_crypt: registered algorithm 'NULL'
Oct 29 20:58:32 hot1 kernel: [17179657.620000] wlan0: no IPv6 routers present
Oct 29 21:02:33 hot1 kernel: [17179898.236000] wlan0: no IPv6 routers present
kern.log.0>>>>
Oct 29 11:42:47 hot1 kernel: [17179833.972000] IPv6 over IPv4 tunneling driver
Oct 29 11:42:58 hot1 kernel: [17179844.940000] wlan0: no IPv6 routers present
Oct 29 11:48:13 hot1 kernel: [17180159.996000] wlan0: Initial auth_alg=0
Oct 29 11:48:13 hot1 kernel: [17180159.996000] wlan0: authenticate with AP 00:a0:c5:ed:b9:9c
Oct 29 11:48:13 hot1 kernel: [17180160.196000] wlan0: authenticate with AP 00:a0:c5:ed:b9:9c
Oct 29 11:48:13 hot1 kernel: [17180160.396000] wlan0: authenticate with AP 00:a0:c5:ed:b9:9c
Oct 29 11:48:14 hot1 kernel: [17180160.596000] wlan0: authentication with AP 00:a0:c5:ed:b9:9c timed out
Oct 29 11:48:38 hot1 kernel: [17180184.996000] rt61pci->rt61pci_init_bbp: Error - BBP register access failed, aborting.
Oct 29 11:48:38 hot1 kernel: [17180184.996000] rt61pci->rt61pci_enable_radio: Error - Register initialization failed.
Oct 29 11:48:51 hot1 kernel: [17180197.596000] wlan0: no IPv6 routers present
Oct 29 11:49:23 hot1 kernel: [17180229.584000] NET: Registered protocol family 17
interfaces>>>>>
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface wlan0 inet dhcp
	address 192.168.1.36
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid Wireless
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	wireless-key s:



auto wlan0

lsmod>>>>>
paco@hot1:~$ lsmod
Module                  Size  Used by
ipv6                  272288  10 
capifs                  7176  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
nls_utf8                3200  2 
ntfs                  112116  2 
nls_iso8859_1           5248  3 
nls_cp437               6912  3 
vfat                   14720  3 
fat                    56348  1 vfat
af_packet              24584  2 
lp                     12964  0 
ieee80211              35272  0 
ieee80211_crypt         7552  1 ieee80211
snd_cmipci             38304  1 
gameport               17160  1 snd_cmipci
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
tsdev                   9152  0 
snd_pcm                84612  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12288  1 snd_cmipci
snd_timer              25348  2 snd_pcm,snd_opl3_lib
snd_hwdep              10756  1 snd_opl3_lib
snd_mpu401_uart        10240  1 snd_cmipci
snd_rawmidi            27264  1 snd_mpu401_uart
snd_seq_device          9868  2 snd_opl3_lib,snd_rawmidi
floppy                 63044  0 
psmouse                41352  0 
serio_raw               8452  0 
usblp                  15488  0 
snd                    58372  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
evdev                  11392  1 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
usbhid                 45152  0 
pcspkr                  4352  0 
soundcore              11232  1 snd
arc4                    3200  1 
rate_control            6784  0 
rt61pci                37632  0 
80211                 175880  2 rate_control,rt61pci
crc_itu_t               3200  1 rt61pci
i2c_viapro              9876  0 
i2c_core               23424  2 i2c_ec,i2c_viapro
via_agp                11264  1 
agpgart                34888  1 via_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  2 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  5 usblp,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_disk               18560  10 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
via82cxxx              10500  0 [permanent]
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
paco@hot1:~$ 

messages.0>>>>>>
Oct 29 11:39:23 hot1 kernel: [17179598.352000] Loading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).

Oct 29 11:42:47 hot1 kernel: [17179833.968000] NET: Registered protocol family 10
Oct 29 11:42:47 hot1 kernel: [17179833.972000] lo: Disabled Privacy Extensions
Oct 29 11:42:47 hot1 kernel: [17179833.972000] IPv6 over IPv4 tunneling driver
Oct 29 11:45:34 hot1 exiting on signal 15

udev_log>>>>>>>>
EVENT[1162155461.079387] add@/module/rt61pci
ACTION=add
DEVPATH=/module/rt61pci
SUBSYSTEM=module
SEQNUM=2150

UEVENT[1162155461.085288] add@/bus/pci/drivers/rt61pci
ACTION=add
DEVPATH=/bus/pci/drivers/rt61pci
SUBSYSTEM=drivers
SEQNUM=2151

UEVENT[1162155461.093349] add@/class/ieee80211/phy0
ACTION=add
DEVPATH=/class/ieee80211/phy0
SUBSYSTEM=ieee80211
SEQNUM=2152
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
IEEE80211_DEV=phy0

UEVENT[1162155461.098784] add@/class/net/wmaster0
ACTION=add
DEVPATH=/class/net/wmaster0
SUBSYSTEM=net
SEQNUM=2153
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
INTERFACE=wmaster0

UEVENT[1162155461.222330] add@/module/rate_control
ACTION=add
DEVPATH=/module/rate_control
SUBSYSTEM=module
SEQNUM=2154

UEVENT[1162155461.293970] add@/module/arc4
UDEV  [1162155461.293970] add@/devices/pnp0/00:03
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:03
SUBSYSTEM=pnp
SEQNUM=2088
PHYSDEVBUS=pnp
UDEVD_EVENT=1

UEVENT[1162155461.299905] add@/class/net/wlan0
ACTION=add
DEVPATH=/class/net/wlan0
SUBSYSTEM=net
SEQNUM=2156
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
INTERFACE=wlan0

UDEV  [1162155461.308295] add@/devices/pci0000:00/0000:00:0a.0
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0a.0
SUBSYSTEM=pci
SEQNUM=2074
PHYSDEVBUS=pci
PCI_CLASS=28000
PCI_ID=1814:0302
PCI_SUBSYS_ID=1814:2561
PCI_SLOT_NAME=0000:00:0a.0
MODALIAS=pci:v00001814d00000302sv00001814sd00002561bc02sc80i00
UDEVD_EVENT=1

UEVENT[1162155461.313646] add@/class/firmware/0000:00:0a.0
ACTION=add
DEVPATH=/class/firmware/0000:00:0a.0
SUBSYSTEM=firmware
SEQNUM=2157
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
FIRMWARE=rt2561s.bin
TIMEOUT=10

UDEV  [1162155461.347391] add@/devices/pnp0/00:04
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:04
SUBSYSTEM=pnp
SEQNUM=2089
PHYSDEVBUS=pnp
UDEVD_EVENT=1

UDEV  [1162155461.532993] add@/devices/pnp0/00:06
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:06
SUBSYSTEM=pnp
SEQNUM=2091
PHYSDEVBUS=pnp
UDEVD_EVENT=1

UDEV  [1162155461.685527] add@/devices/pnp0/00:02
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:02
SUBSYSTEM=pnp
SEQNUM=2087
PHYSDEVBUS=pnp
PHYSDEVDRIVER=system
UDEVD_EVENT=1

UDEV  [1162155461.697442] add@/block/hdb/hdb4
UDEV_LOG=3
ACTION=add
DEVPATH=/block/hdb/hdb4
SUBSYSTEM=block
SEQNUM=2042
MINOR=68
MAJOR=3
PHYSDEVPATH=/devices/pci0000:00/0000:00:07.1/ide0/0.1
PHYSDEVBUS=ide
PHYSDEVDRIVER=ide-disk
UDEVD_EVENT=1
ID_TYPE=disk
ID_MODEL=Maxtor_6E040L0
ID_SERIAL=E1KQ4VRE
ID_REVISION=NAR61590
ID_BUS=ata
ID_PATH=pci-0000:00:07.1-ide-0:1
DEVLINKS=/dev/disk/by-id/ata-Maxtor_6E040L0_E1KQ4VRE-part4 /dev/disk/by-path/pci-0000:00:07.1-ide-0:1-part4
DEVNAME=/dev/hdb4

UDEV  [1162155461.950176] add@/block/hdc
UDEV_LOG=3
ACTION=add
DEVPATH=/block/hdc
SUBSYSTEM=block
SEQNUM=2044
MINOR=0
MAJOR=22
PHYSDEVPATH=/devices/pci0000:00/0000:00:07.1/ide1/1.0
PHYSDEVBUS=ide
PHYSDEVDRIVER=ide-cdrom
UDEVD_EVENT=1
ID_CDROM=1
ID_CDROM_DVD=1
ID_CDROM_MRW=1
ID_CDROM_MRW_W=1
ID_TYPE=cd
ID_MODEL=HL-DT-STDVD-ROM_GDR8163B
ID_SERIAL=
ID_REVISION=0L15
ID_BUS=ata
ID_PATH=pci-0000:00:07.1-ide-1:0
DEVLINKS=/dev/cdrom /dev/dvd /dev/disk/by-path/pci-0000:00:07.1-ide-1:0
DEVNAME=/dev/hdc

UDEV  [1162155462.058507] add@/devices/pnp0/00:08
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:08
SUBSYSTEM=pnp
SEQNUM=2093
PHYSDEVBUS=pnp
PHYSDEVDRIVER=serial
UDEVD_EVENT=1

UDEV  [1162155462.066317] add@/devices/pci0000:00/0000:00:07.2/usb1/1-2
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:07.2/usb1/1-2
SUBSYSTEM=usb
SEQNUM=2100
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
UDEVD_EVENT=1

UDEV  [1162155462.207169] add@/devices/pnp0/00:09
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:09
SUBSYSTEM=pnp
SEQNUM=2094
PHYSDEVBUS=pnp
PHYSDEVDRIVER=serial
UDEVD_EVENT=1

UEVENT[1162155462.372051] add@/module/soundcore
ACTION=add
DEVPATH=/module/soundcore
SUBSYSTEM=module
SEQNUM=2158

UDEV  [1162155462.380919] add@/devices/pci0000:00/0000:00:0c.1/usb3/3-2
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3/3-2
SUBSYSTEM=usb
SEQNUM=2104
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
UDEVD_EVENT=1

UEVENT[1162155462.523455] add@/module/pcspkr
ACTION=add
DEVPATH=/module/pcspkr
SUBSYSTEM=module
SEQNUM=2159

UEVENT[1162155462.530666] add@/bus/platform/drivers/pcspkr
ACTION=add
DEVPATH=/bus/platform/drivers/pcspkr
SUBSYSTEM=drivers
SEQNUM=2160

UEVENT[1162155462.530945] add@/class/input/input1
ACTION=add
DEVPATH=/class/input/input1
SUBSYSTEM=input
SEQNUM=2161
PHYSDEVPATH=/devices/platform/pcspkr
PHYSDEVBUS=platform
PHYSDEVDRIVER=pcspkr
PRODUCT=10/1f/1/100
NAME="PC Speaker"
PHYS="isa0061/input0"
EV=40001
SND=6
MODALIAS=input:b0010v001Fp0001e0100-e0,12,kramls1,2,fw

UDEV  [1162155462.532552] add@/devices/pnp0/00:05
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:05
SUBSYSTEM=pnp
SEQNUM=2090
PHYSDEVBUS=pnp
UDEVD_EVENT=1

UDEV  [1162155462.546928] add@/class/misc/hpet
UDEV_LOG=3
ACTION=add
DEVPATH=/class/misc/hpet
SUBSYSTEM=misc
SEQNUM=2113
MAJOR=10
MINOR=228
UDEVD_EVENT=1
DEVNAME=/dev/hpet

UDEV  [1162155462.548923] add@/class/misc/psaux
UDEV_LOG=3
ACTION=add
DEVPATH=/class/misc/psaux
SUBSYSTEM=misc
SEQNUM=2114
MAJOR=10
MINOR=1
UDEVD_EVENT=1
DEVNAME=/dev/psaux

UDEV  [1162155462.555768] add@/class/misc/snapshot
UDEV_LOG=3
ACTION=add
DEVPATH=/class/misc/snapshot
SUBSYSTEM=misc
SEQNUM=2116
MAJOR=10
MINOR=231
UDEVD_EVENT=1
DEVNAME=/dev/snapshot

UDEV  [1162155462.687616] add@/devices/pci0000:00/0000:00:0c.0/usb2/2-0:1.0
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0c.0/usb2/2-0:1.0
SUBSYSTEM=usb
SEQNUM=2102
PHYSDEVBUS=usb
PHYSDEVDRIVER=hub
DEVICE=/proc/bus/usb/002/001
PRODUCT=0/0/206
TYPE=9/0/0
INTERFACE=9/0/0
MODALIAS=usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00
UDEVD_EVENT=1

UDEV  [1162155462.882868] add@/devices/pci0000:00/0000:00:0c.1/usb3/3-0:1.0
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3/3-0:1.0
SUBSYSTEM=usb
SEQNUM=2103
PHYSDEVBUS=usb
PHYSDEVDRIVER=hub
DEVICE=/proc/bus/usb/003/001
PRODUCT=0/0/206
TYPE=9/0/0
INTERFACE=9/0/0
MODALIAS=usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00
UDEVD_EVENT=1

UEVENT[1162155462.934451] add@/module/usbhid
ACTION=add
DEVPATH=/module/usbhid
SUBSYSTEM=module
SEQNUM=2162

UEVENT[1162155462.934876] add@/bus/usb/drivers/hiddev
ACTION=add
DEVPATH=/bus/usb/drivers/hiddev
SUBSYSTEM=drivers
SEQNUM=2163

UEVENT[1162155462.935022] add@/bus/usb/drivers/usbhid
ACTION=add
DEVPATH=/bus/usb/drivers/usbhid
SUBSYSTEM=drivers
SEQNUM=2164

UEVENT[1162155462.950958] add@/class/input/input2
ACTION=add
DEVPATH=/class/input/input2
SUBSYSTEM=input
SEQNUM=2165
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3/3-2/3-2:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usbhid
PRODUCT=3/46d/c00e/1110
NAME="Logitech USB-PS/2 Optical Mouse"
PHYS="usb-0000:00:0c.1-2/input0"
UNIQ=""
EV=7
KEY=70000 0 0 0 0 0 0 0 0
REL=103
MODALIAS=input:b0003v046DpC00Ee1110-e0,1,2,k110,111,112,r0,1,8,amlsfw

UEVENT[1162155462.951197] add@/class/input/input2/mouse0
ACTION=add
DEVPATH=/class/input/input2/mouse0
SUBSYSTEM=input
SEQNUM=2166
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3/3-2/3-2:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usbhid
MAJOR=13
MINOR=32

UDEV  [1162155462.952671] add@/devices/pci0000:00/0000:00:0c.1/usb3/3-2/3-2:1.0
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3/3-2/3-2:1.0
SUBSYSTEM=usb
SEQNUM=2105
PHYSDEVBUS=usb
DEVICE=/proc/bus/usb/003/002
PRODUCT=46d/c00e/1110
TYPE=0/0/0
INTERFACE=3/1/2
MODALIAS=usb:v046DpC00Ed1110dc00dsc00dp00ic03isc01ip02
UDEVD_EVENT=1

UDEV  [1162155463.149397] add@/devices/platform/i8042/serio1
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/platform/i8042/serio1
SUBSYSTEM=serio
SEQNUM=2098
PHYSDEVBUS=serio
PHYSDEVDRIVER=atkbd
SERIO_TYPE=06
SERIO_PROTO=00
SERIO_ID=00
SERIO_EXTRA=00
MODALIAS=serio:ty06pr00id00ex00
UDEVD_EVENT=1

UDEV  [1162155463.226143] add@/block/hdb/hdb5
UDEV_LOG=3
ACTION=add
DEVPATH=/block/hdb/hdb5
SUBSYSTEM=block
SEQNUM=2043
MINOR=69
MAJOR=3
PHYSDEVPATH=/devices/pci0000:00/0000:00:07.1/ide0/0.1
PHYSDEVBUS=ide
PHYSDEVDRIVER=ide-disk
UDEVD_EVENT=1
ID_TYPE=disk
ID_MODEL=Maxtor_6E040L0
ID_SERIAL=E1KQ4VRE
ID_REVISION=NAR61590
ID_BUS=ata
ID_PATH=pci-0000:00:07.1-ide-0:1
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT32
ID_FS_UUID=6878-ECFB
ID_FS_LABEL=AUDIT
ID_FS_LABEL_SAFE=AUDIT
DEVLINKS=/dev/disk/by-id/ata-Maxtor_6E040L0_E1KQ4VRE-part5 /dev/disk/by-path/pci-0000:00:07.1-ide-0:1-part5 /dev/disk/by-uuid/6878-ECFB /dev/disk/by-label/AUDIT
DEVNAME=/dev/hdb5

UEVENT[1162155463.242620] remove@/class/firmware/0000:00:0a.0
ACTION=remove
DEVPATH=/class/firmware/0000:00:0a.0
SUBSYSTEM=firmware
SEQNUM=2167
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
FIRMWARE=rt2561s.bin
TIMEOUT=10

UDEV  [1162155463.244102] add@/class/firmware/0000:00:0a.0
UDEV_LOG=3
ACTION=add
DEVPATH=/class/firmware/0000:00:0a.0
SUBSYSTEM=firmware
SEQNUM=2157
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
FIRMWARE=rt2561s.bin
TIMEOUT=10
UDEVD_EVENT=1

UDEV  [1162155463.258960] add@/block/hdb/hdb1
UDEV_LOG=3
ACTION=add
DEVPATH=/block/hdb/hdb1
SUBSYSTEM=block
SEQNUM=2039
MINOR=65
MAJOR=3
PHYSDEVPATH=/devices/pci0000:00/0000:00:07.1/ide0/0.1
PHYSDEVBUS=ide
PHYSDEVDRIVER=ide-disk
UDEVD_EVENT=1
ID_TYPE=disk
ID_MODEL=Maxtor_6E040L0
ID_SERIAL=E1KQ4VRE
ID_REVISION=NAR61590
ID_BUS=ata
ID_PATH=pci-0000:00:07.1-ide-0:1
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=31650b2f-4a7a-4e82-a4cb-644ab8548a2c
ID_FS_LABEL=
ID_FS_LABEL_SAFE=
DEVLINKS=/dev/disk/by-id/ata-Maxtor_6E040L0_E1KQ4VRE-part1 /dev/disk/by-path/pci-0000:00:07.1-ide-0:1-part1 /dev/disk/by-uuid/31650b2f-4a7a-4e82-a4cb-644ab8548a2c
DEVNAME=/dev/hdb1

UDEV  [1162155463.297551] add@/devices/pci0000:00/0000:00:07.2/usb1/1-0:1.0
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:07.2/usb1/1-0:1.0
SUBSYSTEM=usb
SEQNUM=2099
PHYSDEVBUS=usb
PHYSDEVDRIVER=hub
DEVICE=/proc/bus/usb/001/001
PRODUCT=0/0/206
TYPE=9/0/0
INTERFACE=9/0/0
MODALIAS=usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00
UDEVD_EVENT=1

UDEV  [1162155463.352652] add@/devices/pnp0/00:0b
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:0b
SUBSYSTEM=pnp
SEQNUM=2096
PHYSDEVBUS=pnp
PHYSDEVDRIVER=i8042 kbd
UDEVD_EVENT=1

UEVENT[1162155463.381054] add@/module/parport
ACTION=add
DEVPATH=/module/parport
SUBSYSTEM=module
SEQNUM=2168

UDEV  [1162155463.382389] add@/class/net/lo
UDEV_LOG=3
ACTION=add
DEVPATH=/class/net/lo
SUBSYSTEM=net
SEQNUM=2117
INTERFACE=lo
UDEVD_EVENT=1

UDEV  [1162155463.384076] add@/class/pci_bus/0000:00
UDEV_LOG=3
ACTION=add
DEVPATH=/class/pci_bus/0000:00
SUBSYSTEM=pci_bus
SEQNUM=2118
UDEVD_EVENT=1

UDEV  [1162155463.385389] add@/class/pci_bus/0000:01
UDEV_LOG=3
ACTION=add
DEVPATH=/class/pci_bus/0000:01
SUBSYSTEM=pci_bus
SEQNUM=2119
UDEVD_EVENT=1

UDEV  [1162155463.387427] add@/class/vc/vcs
UDEV_LOG=3
ACTION=add
DEVPATH=/class/vc/vcs
SUBSYSTEM=vc
SEQNUM=2130
MAJOR=7
MINOR=0
UDEVD_EVENT=1
DEVNAME=/dev/vcs

UDEV  [1162155463.390116] add@/class/vc/vcs1
UDEV_LOG=3
ACTION=add
DEVPATH=/class/vc/vcs1
SUBSYSTEM=vc
SEQNUM=2131
MAJOR=7
MINOR=1
UDEVD_EVENT=1
DEVNAME=/dev/vcs1

UEVENT[1162155463.401926] add@/module/parport_pc
ACTION=add
DEVPATH=/module/parport_pc
SUBSYSTEM=module
SEQNUM=2169

UEVENT[1162155463.401997] add@/bus/pnp/drivers/parport_pc
ACTION=add
DEVPATH=/bus/pnp/drivers/parport_pc
SUBSYSTEM=drivers
SEQNUM=2170

UDEV  [1162155463.404165] add@/class/vc/vcs8
UDEV_LOG=3
ACTION=add
DEVPATH=/class/vc/vcs8
SUBSYSTEM=vc
SEQNUM=2132
MAJOR=7
MINOR=8
UDEVD_EVENT=1
DEVNAME=/dev/vcs8

UEVENT[1162155463.495895] add@/bus/pci/drivers/parport_pc
UDEV  [1162155463.495895] add@/devices/pnp0/00:0a
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:0a
SUBSYSTEM=pnp
SEQNUM=2095
PHYSDEVBUS=pnp
UDEVD_EVENT=1

UDEV  [1162155463.567506] add@/devices/pci0000:00/0000:00:0c.2/usb4/4-0:1.0
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0c.2/usb4/4-0:1.0
SUBSYSTEM=usb
SEQNUM=2106
PHYSDEVBUS=usb
PHYSDEVDRIVER=hub
DEVICE=/proc/bus/usb/004/001
PRODUCT=0/0/206
TYPE=9/0/1
INTERFACE=9/0/0
MODALIAS=usb:v0000p0000d0206dc09dsc00dp01ic09isc00ip00
UDEVD_EVENT=1

UDEV  [1162155463.578115] add@/class/vc/vcsa
UDEV_LOG=3
ACTION=add
DEVPATH=/class/vc/vcsa
SUBSYSTEM=vc
SEQNUM=2133
MAJOR=7
MINOR=128
UDEVD_EVENT=1
DEVNAME=/dev/vcsa

UDEV  [1162155463.580392] add@/class/vc/vcsa1
UDEV_LOG=3
ACTION=add
DEVPATH=/class/vc/vcsa1
SUBSYSTEM=vc
SEQNUM=2134
MAJOR=7
MINOR=129
UDEVD_EVENT=1
DEVNAME=/dev/vcsa1

UDEV  [1162155463.582555] add@/class/vc/vcsa8
UDEV_LOG=3
ACTION=add
DEVPATH=/class/vc/vcsa8
SUBSYSTEM=vc
SEQNUM=2135
MAJOR=7
MINOR=136
UDEVD_EVENT=1
DEVNAME=/dev/vcsa8

UDEV  [1162155463.583939] add@/module/pci_hotplug
UDEV_LOG=3
ACTION=add
DEVPATH=/module/pci_hotplug
SUBSYSTEM=module
SEQNUM=2136
UDEVD_EVENT=1

UDEV  [1162155463.585218] add@/module/shpchp
UDEV_LOG=3
ACTION=add
DEVPATH=/module/shpchp
SUBSYSTEM=module
SEQNUM=2137
UDEVD_EVENT=1

UDEV  [1162155463.586560] add@/bus/pci/drivers/shpchp
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/pci/drivers/shpchp
SUBSYSTEM=drivers
SEQNUM=2138
UDEVD_EVENT=1

UEVENT[1162155463.602438] add@/module/evdev
ACTION=add
DEVPATH=/module/evdev
SUBSYSTEM=module
SEQNUM=2172

UEVENT[1162155463.603009] add@/class/input/input0/event0
ACTION=add
DEVPATH=/class/input/input0/event0
SUBSYSTEM=input
SEQNUM=2173
PHYSDEVPATH=/devices/platform/i8042/serio1
PHYSDEVBUS=serio
PHYSDEVDRIVER=atkbd
MAJOR=13
MINOR=64

UEVENT[1162155463.603162] add@/class/input/input1/event1
ACTION=add
DEVPATH=/class/input/input1/event1
SUBSYSTEM=input
SEQNUM=2174
PHYSDEVPATH=/devices/platform/pcspkr
PHYSDEVBUS=platform
PHYSDEVDRIVER=pcspkr
MAJOR=13
MINOR=65

UEVENT[1162155463.603321] add@/class/input/input2/event2
ACTION=add
DEVPATH=/class/input/input2/event2
SUBSYSTEM=input
SEQNUM=2175
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3/3-2/3-2:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usbhid
MAJOR=13
MINOR=66

UDEV  [1162155463.650134] add@/class/input/mice
UDEV_LOG=3
ACTION=add
DEVPATH=/class/input/mice
SUBSYSTEM=input
SEQNUM=2112
MAJOR=13
MINOR=63
UDEVD_EVENT=1
DEVNAME=/dev/input/mice

UDEV  [1162155463.675909] add@/bus/pci/drivers/agpgart-via
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/pci/drivers/agpgart-via
SUBSYSTEM=drivers
SEQNUM=2141
UDEVD_EVENT=1

UDEV  [1162155463.678752] add@/class/misc/agpgart
UDEV_LOG=3
ACTION=add
DEVPATH=/class/misc/agpgart
SUBSYSTEM=misc
SEQNUM=2142
MAJOR=10
MINOR=175
UDEVD_EVENT=1
DEVNAME=/dev/agpgart

UDEV  [1162155463.680522] add@/module/i2c_core
UDEV_LOG=3
ACTION=add
DEVPATH=/module/i2c_core
SUBSYSTEM=module
SEQNUM=2143
UDEVD_EVENT=1

UDEV  [1162155463.682299] add@/bus/i2c/drivers/i2c_adapter
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/i2c/drivers/i2c_adapter
SUBSYSTEM=drivers
SEQNUM=2144
UDEVD_EVENT=1

UDEV  [1162155463.684166] add@/module/i2c_viapro
UDEV_LOG=3
ACTION=add
DEVPATH=/module/i2c_viapro
SUBSYSTEM=module
SEQNUM=2145
UDEVD_EVENT=1

UDEV  [1162155463.685901] add@/bus/pci/drivers/vt596_smbus
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/pci/drivers/vt596_smbus
SUBSYSTEM=drivers
SEQNUM=2146
UDEVD_EVENT=1

UDEV  [1162155463.691252] add@/module/agpgart
UDEV_LOG=3
ACTION=add
DEVPATH=/module/agpgart
SUBSYSTEM=module
SEQNUM=2139
UDEVD_EVENT=1

UDEV  [1162155463.697980] add@/class/i2c-adapter/i2c-0
UDEV_LOG=3
ACTION=add
DEVPATH=/class/i2c-adapter/i2c-0
SUBSYSTEM=i2c-adapter
SEQNUM=2147
PHYSDEVPATH=/devices/pci0000:00/0000:00:07.3/i2c-0
PHYSDEVDRIVER=i2c_adapter
UDEVD_EVENT=1

UDEV  [1162155463.699966] add@/module/crc_itu_t
UDEV_LOG=3
ACTION=add
DEVPATH=/module/crc_itu_t
SUBSYSTEM=module
SEQNUM=2148
UDEVD_EVENT=1

UDEV  [1162155463.701712] add@/module/80211
UDEV_LOG=3
ACTION=add
DEVPATH=/module/80211
SUBSYSTEM=module
SEQNUM=2149
UDEVD_EVENT=1

UDEV  [1162155463.703541] add@/module/rt61pci
UDEV_LOG=3
ACTION=add
DEVPATH=/module/rt61pci
SUBSYSTEM=module
SEQNUM=2150
UDEVD_EVENT=1

UDEV  [1162155463.705305] add@/bus/pci/drivers/rt61pci
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/pci/drivers/rt61pci
SUBSYSTEM=drivers
SEQNUM=2151
UDEVD_EVENT=1

UDEV  [1162155463.707175] add@/class/ieee80211/phy0
UDEV_LOG=3
ACTION=add
DEVPATH=/class/ieee80211/phy0
SUBSYSTEM=ieee80211
SEQNUM=2152
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
IEEE80211_DEV=phy0
UDEVD_EVENT=1

UDEV  [1162155463.708611] add@/module/via_agp
UDEV_LOG=3
ACTION=add
DEVPATH=/module/via_agp
SUBSYSTEM=module
SEQNUM=2140
UDEVD_EVENT=1

UEVENT[1162155463.729091] add@/module/snd
ACTION=add
DEVPATH=/module/snd
SUBSYSTEM=module
SEQNUM=2176

UDEV  [1162155463.733841] add@/module/rate_control
UDEV_LOG=3
ACTION=add
DEVPATH=/module/rate_control
SUBSYSTEM=module
SEQNUM=2154
UDEVD_EVENT=1

UDEV  [1162155463.736112] add@/module/arc4
UDEV_LOG=3
ACTION=add
DEVPATH=/module/arc4
SUBSYSTEM=module
SEQNUM=2155
UDEVD_EVENT=1

UDEV  [1162155463.754350] add@/class/net/wlan0
UDEV_LOG=3
ACTION=add
DEVPATH=/class/net/wlan0
SUBSYSTEM=net
SEQNUM=2156
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
INTERFACE=wlan0
UDEVD_EVENT=1

UEVENT[1162155463.760864] add@/module/usblp
ACTION=add
DEVPATH=/module/usblp
SUBSYSTEM=module
SEQNUM=2177

UEVENT[1162155463.761264] add@/bus/usb/drivers/usblp
ACTION=add
DEVPATH=/bus/usb/drivers/usblp
SUBSYSTEM=drivers
SEQNUM=2178

UDEV  [1162155463.765315] add@/module/soundcore
UDEV_LOG=3
ACTION=add
DEVPATH=/module/soundcore
SUBSYSTEM=module
SEQNUM=2158
UDEVD_EVENT=1

UDEV  [1162155463.767436] add@/module/pcspkr
UDEV_LOG=3
ACTION=add
DEVPATH=/module/pcspkr
SUBSYSTEM=module
SEQNUM=2159
UDEVD_EVENT=1

UEVENT[1162155463.771675] add@/class/usb/lp0
ACTION=add
DEVPATH=/class/usb/lp0
SUBSYSTEM=usb
SEQNUM=2179
PHYSDEVPATH=/devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usblp
MAJOR=180
MINOR=0

UDEV  [1162155463.779602] add@/devices/pci0000:00/0000:00:0c.0/usb2
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0c.0/usb2
SUBSYSTEM=usb
SEQNUM=2108
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
UDEVD_EVENT=1

UDEV  [1162155463.784029] add@/devices/pci0000:00/0000:00:0c.1/usb3
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3
SUBSYSTEM=usb
SEQNUM=2109
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
UDEVD_EVENT=1

UEVENT[1162155463.788856] add@/module/serio_raw
ACTION=add
DEVPATH=/module/serio_raw
SUBSYSTEM=module
SEQNUM=2180

UEVENT[1162155463.789562] add@/bus/serio/drivers/serio_raw
ACTION=add
DEVPATH=/bus/serio/drivers/serio_raw
SUBSYSTEM=drivers
SEQNUM=2181

UDEV  [1162155463.836123] add@/devices/pci0000:00/0000:00:0c.2/usb4
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0c.2/usb4
SUBSYSTEM=usb
SEQNUM=2110
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
UDEVD_EVENT=1

UDEV  [1162151860.002659] add@/class/misc/rtc
UDEV_LOG=3
ACTION=add
DEVPATH=/class/misc/rtc
SUBSYSTEM=misc
SEQNUM=2115
MAJOR=10
MINOR=135
UDEVD_EVENT=1
DEVNAME=/dev/rtc

UDEV  [1162151860.006852] add@/bus/platform/drivers/pcspkr
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/platform/drivers/pcspkr
SUBSYSTEM=drivers
SEQNUM=2160
UDEVD_EVENT=1

UEVENT[1162151860.016970] add@/module/psmouse
ACTION=add
DEVPATH=/module/psmouse
SUBSYSTEM=module
SEQNUM=2182

UEVENT[1162151860.018251] add@/bus/serio/drivers/psmouse
ACTION=add
DEVPATH=/bus/serio/drivers/psmouse
SUBSYSTEM=drivers
SEQNUM=2183

UDEV  [1162151860.020530] add@/devices/platform/i8042/serio0
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/platform/i8042/serio0
SUBSYSTEM=serio
SEQNUM=2097
PHYSDEVBUS=serio
SERIO_TYPE=01
SERIO_PROTO=00
SERIO_ID=00
SERIO_EXTRA=00
MODALIAS=serio:ty01pr00id00ex00
UDEVD_EVENT=1

UDEV  [1162151860.030683] add@/class/usb_device/usbdev2.1
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_device/usbdev2.1
SUBSYSTEM=usb_device
SEQNUM=2122
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.0/usb2
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
MAJOR=189
MINOR=128
UDEVD_EVENT=1
USB_BUS=002
USB_DEV=001
DEVNAME=/dev/bus/usb/002/001

UDEV  [1162151860.039695] add@/class/usb_device/usbdev3.1
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_device/usbdev3.1
SUBSYSTEM=usb_device
SEQNUM=2123
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
MAJOR=189
MINOR=256
UDEVD_EVENT=1
USB_BUS=003
USB_DEV=001
DEVNAME=/dev/bus/usb/003/001

UDEV  [1162151860.048611] add@/class/usb_device/usbdev3.2
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_device/usbdev3.2
SUBSYSTEM=usb_device
SEQNUM=2124
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.1/usb3/3-2
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
MAJOR=189
MINOR=257
UDEVD_EVENT=1
USB_BUS=003
USB_DEV=002
DEVNAME=/dev/bus/usb/003/002

UDEV  [1162151860.057414] add@/class/usb_device/usbdev4.1
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_device/usbdev4.1
SUBSYSTEM=usb_device
SEQNUM=2125
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.2/usb4
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
MAJOR=189
MINOR=384
UDEVD_EVENT=1
USB_BUS=004
USB_DEV=001
DEVNAME=/dev/bus/usb/004/001

UDEV  [1162151860.059562] add@/class/usb_host/usb_host2
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_host/usb_host2
SUBSYSTEM=usb_host
SEQNUM=2127
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=uhci_hcd
UDEVD_EVENT=1

UDEV  [1162151860.061519] add@/class/usb_host/usb_host3
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_host/usb_host3
SUBSYSTEM=usb_host
SEQNUM=2128
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.1
PHYSDEVBUS=pci
PHYSDEVDRIVER=uhci_hcd
UDEVD_EVENT=1

UDEV  [1162151860.063909] add@/class/usb_host/usb_host4
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_host/usb_host4
SUBSYSTEM=usb_host
SEQNUM=2129
PHYSDEVPATH=/devices/pci0000:00/0000:00:0c.2
PHYSDEVBUS=pci
PHYSDEVDRIVER=ehci_hcd
UDEVD_EVENT=1

UEVENT[1162151860.128160] add@/module/floppy
ACTION=add
DEVPATH=/module/floppy
SUBSYSTEM=module
SEQNUM=2184

UDEV  [1162151860.171911] add@/devices/pci0000:00/0000:00:07.1
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:07.1
SUBSYSTEM=pci
SEQNUM=2070
PHYSDEVBUS=pci
PHYSDEVDRIVER=VIA_IDE
PCI_CLASS=1018A
PCI_ID=1106:0571
PCI_SUBSYS_ID=0000:0000
PCI_SLOT_NAME=0000:00:07.1
MODALIAS=pci:v00001106d00000571sv00000000sd00000000bc01sc01i8a
UDEVD_EVENT=1

UDEV  [1162151860.174247] add@/module/usbhid
UDEV_LOG=3
ACTION=add
DEVPATH=/module/usbhid
SUBSYSTEM=module
SEQNUM=2162
UDEVD_EVENT=1

UEVENT[1162151860.213369] add@/devices/platform/floppy.0
ACTION=add
DEVPATH=/devices/platform/floppy.0
SUBSYSTEM=platform
SEQNUM=2185
PHYSDEVBUS=platform

UEVENT[1162151860.213667] add@/block/fd0
ACTION=add
DEVPATH=/block/fd0
SUBSYSTEM=block
SEQNUM=2186
MINOR=0
MAJOR=2
PHYSDEVPATH=/devices/platform/floppy.0
PHYSDEVBUS=platform

UDEV  [1162151860.215072] add@/devices/pnp0/00:07
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:07
SUBSYSTEM=pnp
SEQNUM=2092
PHYSDEVBUS=pnp
UDEVD_EVENT=1

UDEV  [1162151860.234567] add@/bus/usb/drivers/hiddev
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/usb/drivers/hiddev
SUBSYSTEM=drivers
SEQNUM=2163
UDEVD_EVENT=1

UDEV  [1162151860.237647] add@/bus/usb/drivers/usbhid
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/usb/drivers/usbhid
SUBSYSTEM=drivers
SEQNUM=2164
UDEVD_EVENT=1

UDEV  [1162151860.259309] remove@/class/firmware/0000:00:0a.0
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/firmware/0000:00:0a.0
SUBSYSTEM=firmware
SEQNUM=2167
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=rt61pci
FIRMWARE=rt2561s.bin
TIMEOUT=10
UDEVD_EVENT=1

UDEV  [1162151860.262330] add@/module/parport
UDEV_LOG=3
ACTION=add
DEVPATH=/module/parport
SUBSYSTEM=module
SEQNUM=2168
UDEVD_EVENT=1

UDEV  [1162151860.264838] add@/module/parport_pc
UDEV_LOG=3
ACTION=add
DEVPATH=/module/parport_pc
SUBSYSTEM=module
SEQNUM=2169
UDEVD_EVENT=1

too long...........
check the point´s.
Thank´s

---

