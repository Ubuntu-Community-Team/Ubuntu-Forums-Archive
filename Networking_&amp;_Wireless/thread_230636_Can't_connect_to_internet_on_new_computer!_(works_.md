---
title: "Can't connect to internet on new computer! (works in WinXP)"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by mmcmonster on 2006-08-06
Hi.  My computer is set to dual-boot in WinXP and Dapper AMD64.  In WinXP networking works fine, in Dapper I can't get firefox to connect to any site. :-(

I (believe) I am using an ethernet card in the back of the machine.

Here is the output from ifconfig and dhclient:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:05:76:B9
          inet6 addr: fe80::215:58ff:fe05:76b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:17 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:900 (900.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:44092 (43.0 KiB)  TX bytes:44092 (43.0 KiB)

$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:15:58:05:76:b9
Sending on   LPF/eth0/00:15:58:05:76:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
$

```

---

### Post by mmcmonster on 2006-08-06
As an aside, I had the same problem running a Dapper-i386 live CD.

---

### Post by mmcmonster on 2006-08-06
Here is some more information about my system:
```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
```

$ lspci
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
0000:00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:03:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0163 (rev a1)
0000:04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:04:09.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)

``` ```

$ lsmod
Module                  Size  Used by
ipv6                  300416  8
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0
powernow_k8            12992  0
cpufreq_userspace       9184  1
cpufreq_stats           8264  0
freq_table              6464  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
ac                      7176  1 acpi_sbs
nls_utf8                3584  1
ntfs                  101376  1
nls_iso8859_1           6656  1
nls_cp437               8320  1
vfat                   16768  1
fat                    57136  1 vfat
dm_mod                 63176  1
md_mod                 76792  0
sr_mod                 19748  0
sbp2                   28420  0
lp                     15040  0
irtty_sir              11264  0
sir_dev                23928  1 irtty_sir
irda                  221548  2 irtty_sir,sir_dev
crc_ccitt               3584  1 irda
tsdev                  10240  0
parport_pc             40944  1
parport                44172  3 ppdev,lp,parport_pc
floppy                 74120  0
usb_storage            81984  0
usbhid                 42912  0
psmouse                40452  0
nvidia               5433176  0
i2c_core               26624  2 i2c_acpi_ec,nvidia
serio_raw               9732  0
snd_intel8x0           38440  1
snd_ac97_codec        110268  1 snd_intel8x0
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104712  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              29064  1 snd_pcm
pcspkr                  3592  0
snd                    68576  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
snd_page_alloc         13968  2 snd_intel8x0,snd_pcm
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
af_packet              28172  2
sg                     43568  0
evdev                  14464  4
ext3                  145936  2
jbd                    70952  1 ext3
ide_generic             2816  0
ehci_hcd               34568  0
ohci_hcd               23684  0
usbcore               145980  5 usb_storage,usbhid,ehci_hcd,ohci_hcd
forcedeth              27908  0
ohci1394               37452  0
ieee1394              369688  2 sbp2,ohci1394
ide_cd                 35744  0
cdrom                  41144  2 sr_mod,ide_cd
generic                 7300  0
amd74xx                16944  0 [permanent]
sd_mod                 21504  7
sata_nv                12420  11
libata                 86048  1 sata_nv
scsi_mod              160504  6 sr_mod,sbp2,usb_storage,sg,sd_mod,libata
thermal                16524  0
processor              29224  2 powernow_k8,thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
$

```

---

### Post by mmcmonster on 2006-08-06
An update:

While I am still interested in figuring out what is wrong, I bypassed the problem by inserting an ethernet card that I had lying around and just plugged into that. :-)

Just a suggestion to all those out there with "broken" computers:  Sometimes it's worth it to canabalize the hardware if it's not too old.

---

### Post by AndrewShugg on 2006-08-13
Any success yet getting Ubuntu 6.06 and your nForce ethernet working?

Andrew S.

---

### Post by AndrewShugg on 2006-08-13
This article may help:

[https://help.ubuntu.com/community/NvNetInstallation](https://help.ubuntu.com/community/NvNetInstallation)

Andrew S.

---

### Post by AndrewShugg on 2006-08-17
> **mmcmonster said:**
> Hi.  My computer is set to dual-boot in WinXP and Dapper AMD64.  In WinXP networking works fine, in Dapper I can't get firefox to connect to any site. :-(

I (believe) I am using an ethernet card in the back of the machine.


Looks like the same problem I was having, see these threads:

[http://www.ubuntuforums.org/showthread.php?t=231330](http://www.ubuntuforums.org/showthread.php?t=231330)

[http://www.ubuntuforums.org/archive/index.php/t-186848.html](http://www.ubuntuforums.org/archive/index.php/t-186848.html)

Cheers,

Andrew S.

---

