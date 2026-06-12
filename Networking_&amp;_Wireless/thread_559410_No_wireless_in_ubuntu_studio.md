---
title: "No wireless in ubuntu studio"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by bfr666 on 2007-09-25
**EDIT: SOLVED! SORRY TO WASTE YOUR TIME!**

**SOLUTION: sudo apt-get install linux-lowlatency**

Hi! 

I'm complete noob with linux, but i'll try to explain.. 

First i installed Feisty on my amilo pi1505 laptop, and everything worked fine. 
Wireless worked out of the box, so i did not need to configure anything(which was very surprising).

Then i "upgraded" to ubuntu studio, and the wireless died. My network devices only 
show the modem and the "wired" connection. 

However, when i reboot and select the "generic" kernel instead of the new "low latency", the wireless works again. Changing between kde and gnome wont change anything.

Here are the outputs of iwconfig,ifconfig, lspci and lsmod, in that order. This is from the
WORKING configuration. I'll post the same from the non-working later. 

Please help, and let me know if you need any other information.
I'm sure it's just matter of some configuration files, but i dont even know where to start.

EDIT: Please note, that for some reason my wlan is eth1 as you can see, not wlan0(but it works)?

If i have written only bs, i apologize, i'm doing the best i can :)

roni@laptop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"wlan-ap"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:DB:05:A5:2B   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-55 dBm  Noise level=-56 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:200   Missed beacon:0

vbox0     no wireless extensions.

roni@laptop:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:03:0D:59:AC:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4c00 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:76:98:D2  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe76:98d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5428 errors:165 dropped:365 overruns:0 frame:0
          TX packets:3299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3600639 (3.4 MiB)  TX bytes:559902 (546.7 KiB)
          Interrupt:18 Base address:0xe000 Memory:f7000000-f7000fff 

eth0:avah Link encap:Ethernet  HWaddr 00:03:0D:59:AC:26  
          inet addr:169.254.4.151  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8211 (8.0 KiB)  TX bytes:8211 (8.0 KiB)

vbox0     Link encap:Ethernet  HWaddr EE:E4:83:74:79:72  
          inet6 addr: fe80::ece4:83ff:fe74:7972/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

roni@laptop:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
06:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
06:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

roni@laptop:~$ **lsmod**
Module                  Size  Used by
michael_mic             3584  0 
arc4                    2944  0 
ecb                     4480  0 
blkcipher               6784  1 ecb
ieee80211_crypt_tkip    12032  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
ipv6                  268960  14 
bluetooth              55908  4 rfcomm,l2cap
tun                    12032  0 
vboxdrv                54664  0 
ppdev                  10116  0 
i915                   25472  3 
drm                    81044  4 i915
acpi_cpufreq           10056  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
button                  8720  0 
ac                      6020  0 
container               5248  0 
video                  16388  0 
dock                   10268  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
nls_utf8                3072  1 
ntfs                  107764  1 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  1 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
ipw3945               118816  1 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
af_packet              23816  8 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,ieee80211
sdhci                  18700  0 
mmc_core               26756  1 sdhci
serio_raw               7940  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                38920  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              26140  1 
agpgart                35400  3 drm,intel_agp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  5 
generic                 5124  0 [permanent]
8139too                27648  0 
ata_generic             9092  0 
ohci1394               36528  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ieee1394              299448  2 sbp2,ohci1394
ata_piix               15492  0 
ahci                   22020  4 
libata                125720  3 ata_generic,ata_piix,ahci
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  3 ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
roni@laptop:~$

**EDIT: These are the same from the non-working configuration.**
**Help me ubu-wan-kenobi, you're my only hope!**

roni@laptop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

vbox0     no wireless extensions.

roni@laptop:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:03:0D:59:AC:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:03:0D:59:AC:26  
          inet addr:169.254.4.151  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17375 (16.9 KiB)  TX bytes:17375 (16.9 KiB)

vbox0     Link encap:Ethernet  HWaddr 5E:2B:E6:3C:01:18  
          inet6 addr: fe80::5c2b:e6ff:fe3c:118/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

roni@laptop:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
06:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
06:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
roni@laptop:~$ **lsmod**
Module                  Size  Used by
binfmt_misc            13064  1 
rfcomm                 41752  0 
ipv6                  274080  14 
l2cap                  26112  5 rfcomm
bluetooth              57444  4 rfcomm,l2cap
tun                    12032  0 
vboxdrv                54792  0 
ppdev                  10116  0 
i915                   25600  3 
drm                    81812  4 i915
acpi_cpufreq           10568  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7488  0 
cpufreq_ondemand        9356  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12164  0 
pcc_acpi               13184  0 
button                  8720  0 
ac                      6020  0 
container               5248  0 
video                  16260  0 
dock                   10424  0 
battery                10756  0 
sbs                    15528  0 
i2c_ec                  6016  1 sbs
i2c_core               23424  1 i2c_ec
asus_acpi              17308  0 
backlight               6784  1 asus_acpi
nls_utf8                3072  1 
ntfs                  108276  1 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    54044  1 vfat
af_packet              24072  4 
sbp2                   24324  0 
parport_pc             36644  0 
lp                     12548  0 
parport                37576  3 ppdev,parport_pc,lp
fuse                   46996  1 
snd_hda_intel          22168  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            45056  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                80260  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33408  0 
snd_seq_midi            9600  0 
snd_rawmidi            25856  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
8139too                27776  0 
sr_mod                 17188  0 
cdrom                  37664  1 sr_mod
iTCO_wdt               12072  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ipw3945               118944  0 
sdhci                  18828  0 
ieee80211              35272  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
mmc_core               26756  1 sdhci
generic                 5124  0 [permanent]
serio_raw               7940  0 
snd                    54788  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26140  1 
agpgart                35788  3 drm,intel_agp
soundcore               9440  1 snd
psmouse                38792  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
shpchp                 34324  0 
pci_hotplug            33608  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ata_generic             9092  0 
ext3                  134152  1 
jbd                    63528  1 ext3
mbcache                 9604  1 ext3
sg                     35996  0 
sd_mod                 23556  5 
8139cp                 25344  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394              300120  2 sbp2,ohci1394
ahci                   22148  4 
ata_piix               15620  0 
libata                125848  3 ata_generic,ahci,ata_piix
scsi_mod              143116  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               34316  0 
uhci_hcd               25488  0 
usbcore               135048  3 ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31560  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  43296  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
roni@laptop:~$

---

