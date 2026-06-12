---
title: "Dual boot:  XP connects, Linux doesn't"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by uwjames on 2006-10-11
Hello, Linux newbie here.  Been hitting my head on the wall ](*,) for a while and would love some help.  An assortment of data is posted below.

Ubuntu (dapper drake) booted fine off the live CD, connected to internet.  I wiped my drives and set up dual boot (xp and drake).  Using XP now, and works well, but Ubuntu is not connecting.  Tried a few things including blacklisting 8139cp module (interferes with 8139too), and attempted to go for static IP, though I'm not sure how to implement it would rather not.  Interface file is set to DHCP.  Have not tried to turn off IPv6 yet.  PPPoEconf says modem is disconnected (obviously not, xp connects) or another process is interfering (IPv6?).  Last twist.. the first time I ran 
"modprobe 8139too" the card connected and internet worked fine.  but the next time I rebooted the connection did not connect, and could not repro the fix.

hope this is enough information, and if not then here is some terminal spew I generated for your viewing pleasure:

> johndoe@johndoe-desktop:/root$ sudo ifdown eth0

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:e0:18:21:1c:2d
Sending on   LPF/eth0/00:e0:18:21:1c:2d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

----------------------------------------------------------------------------
johndoe@johndoe-desktop:/root$ sudo ifup eth0

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:e0:18:21:1c:2d
Sending on   LPF/eth0/00:e0:18:21:1c:2d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

----------------------------------------------------
johndoe@johndoe-desktop:/root$ lsmod

Module                  Size  Used by
pppoe                  14400  0
pppox                   3720  1 pppoe
ppp_generic            30100  2 pppoe,pppox
slhc                    7424  1 ppp_generic
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
ipv6                  265728  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
floppy                 62148  0
rtc                    13492  0
nvidia               4550772  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd_via82xx            28824  1
gameport               15496  1 snd_via82xx
snd_ac97_codec         93088  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
psmouse                36100  0
serio_raw               7300  0
snd                    55268  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
pcspkr                  2180  0
8139too                26880  0
soundcore              10208  1 snd
mii                     5888  1 8139too
via686a                17672  0
i2c_isa                 4992  1 via686a
i2c_viapro              8980  0
i2c_core               21904  5 i2c_acpi_ec,nvidia,via686a,i2c_isa,i2c_viapro
via_agp                 9856  1
agpgart                34888  2 nvidia,via_agp
ltmodem               566638  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
sg                     37920  0
sd_mod                 19984  2
tsdev                   8000  0
evdev                   9856  1
usbhid                 39904  0
usb_storage            74176  2
scsi_mod              139496  3 sg,sd_mod,usb_storage
ext3                  135688  2
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  4 usbhid,usb_storage,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
via82cxxx               9988  0 [permanent]
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit


--------------------------------------------------
johndoe@johndoe-desktop:/root$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:E0:18:21:1C:2D
          inet6 addr: fe80::2e0:18ff:fe21:1c2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

johndoe@johndoe-desktop:/root$


thanks in advance!!

---

### Post by apjone on 2006-10-11
please do 
cat /etc/network/interfaces

---

### Post by uwjames on 2006-10-11
here are results:

> johndoe@johndoe-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider
johndoe@johndoe-desktop:~$

---

