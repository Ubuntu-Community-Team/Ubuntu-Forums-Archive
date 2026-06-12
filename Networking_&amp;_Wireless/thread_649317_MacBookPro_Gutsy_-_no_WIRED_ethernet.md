---
title: "MacBookPro Gutsy - no WIRED ethernet"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by bryonak on 2007-12-24
Hi guys, how about some variety: instead of complaining about wireless (we'll see about that later...) I'm not even able to get wired ethernet on my Gutsy MacBookPro Santa Rosa.
I just did a fresh install, looking forward to tweaking the hell out of it.. but well, without internet connection... the only "special" thing I did was losing the swap partition in favour of a separate home.
Curiously I'm not even getting it with the live CD.

I'm not able to ping anything, no application can establish a connection. (Timeout)
Here's my output (with the Gutsy HD install)...


lspci
> 
...
0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
...



lsmod
> 
Module                  Size  Used by
nls_utf8                3072  1 
hfsplus                78084  1 
ipv6                  273892  10 
af_packet              24840  2 
hci_usb                18332  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  7 hci_usb,rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
button                  8976  0 
container               5504  0 
sbs                    19592  0 
ac                      6148  0 
dock                   10656  0 
video                  18060  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
joydev                 11328  0 
snd_seq_dummy           4740  0 
uvcvideo               48644  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
sky2                   46852  0 
snd_rawmidi            25728  1 snd_seq_midi
i2c_core               26112  0 
appletouch             10880  0 
xpad                    9988  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  0 
agpgart                35016  1 intel_agp
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
evdev                  11136  7 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_piix               17540  4 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sd_mod,sr_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 hci_usb,uvcvideo,appletouch,xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor



cat /etc/udev/rules.d/70-persisten-net-rules
> 
...
# PCI device 0x11ab:0x436a (sky2)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1b:63:a4:fe:cd", NAME="eth0"



cat /etc/network/interfaces
> 
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0



ifconfig -v -a
> 
eth0      Link encap:Ethernet  HWaddr 00:1B:63:A4:FE:CD  
          inet6 addr: fe80::21b:63ff:fea4:fecd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:646249 (631.1 KB)  TX bytes:5249 (5.1 KB)
          Interrupt:18 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:63:A4:FE:CD  
          inet addr:169.254.10.199  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.1 KB)  TX bytes:8304 (8.1 KB)

Strangely, the received and transferred bytes for **eth0** increase over time


sudo ifup eth0
> 
ifup: interface eth0 is already configured

changes to
> 
Ignoring unknown interface eth0=eth0.

if I set the wired connection in the Network Settings to "roaming mode".


sudo ethtool eth0
> 
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes



sudo dhclient eth0
> 
...
Listening on LPF/eth0/00:1b:63:a4:fe:cd
Sending on LPF/eth0/00:1b:63:a4:fe:cd
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



I don't think it's about IPv6, because "$ dig A ..." doesn't work either.

The CD's MD5 checksum is all right. (desktop-install)

I've tried two different ethernet cables, and tried both on another machine, no error there. It is however possible that my mac's ethernet jack is defunct. How could I check that?

At the moment, my MacBook is pretty useless... Ideas, anyone?

---

### Post by xelapond on 2007-12-25
Does the port work in Mac OS X?

---

### Post by bryonak on 2008-01-02
After putting back OSX (where eth0 was working) I tried installing Ubuntu again - without progress.
Though the hardware and the link are correctly detected, it just didn't work. Then I wanted to try out wireless, installing madwifi and wicd with an USB stick while removing the default network manager in the process.
And now I've got both wired and wireless working.

Well... let's call it solved. (Though "frustrating" also comes to mind ;))

---

