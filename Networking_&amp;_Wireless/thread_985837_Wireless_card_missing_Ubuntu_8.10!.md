---
title: "Wireless card missing Ubuntu 8.10!"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by HishamN on 2008-11-18
Hi,

I had Ubuntu Hardy and I had no problem with wireless, but after upgrading it to 8.10 using alternate CD I faced a problem with my wireless which is connect in first time to AP and it disconnect after 3 mins! then it can't connect again to it.

I red an article and I decided to install linux-backports-modules-intrepid-generic package then after I rebooted my system I checked Network icon on system tray and Wireless option not  there!

I tried several steps to retrieve my wireless but still wireless missing.

BTW if I type lspci on shell the output mention my wireless:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
[COLOR="Red"][SIZE="3"]01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)[/SIZE][/COLOR]
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


Thanks

Regards

---

### Post by HishamN on 2008-11-18
Sorry I didn't see HOWTO post a Wireless issue (ticket).

My Laptop:
Fujitsu siemens Amilo pro v3205.
Ubuntu 8.10

hisham@Hisham-NB:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:36:c5:6a:85  
          inet addr:10.8.48.136  Bcast:10.8.63.255  Mask:255.255.224.0
          inet6 addr: fe80::216:36ff:fec5:6a85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445565 errors:0 dropped:0 overruns:18 frame:18
          TX packets:57397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83116334 (83.1 MB)  TX bytes:15618190 (15.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6997416 (6.9 MB)  TX bytes:6997416 (6.9 MB)

pan0      Link encap:Ethernet  HWaddr ea:e9:42:a3:f1:a6  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

hisham@Hisham-NB:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

hisham@Hisham-NB:~$ lsmod
Module                  Size  Used by
af_packet              25728  2 
btusb                  19736  0 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44432  4 
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  12 rfcomm,bnep
bluetooth              61924  11 btusb,rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
wmi                    14504  0 
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
ipt_LOG                13700  3 
xt_limit               10372  3 
ipt_addrtype           10496  4 
xt_state               10112  2 
xt_tcpudp              11008  7 
xt_conntrack           11904  2 
ip6table_filter        10624  1 
ip6_tables             21008  1 ip6table_filter
ipv6                  263972  10 
nf_nat_irc             10240  0 
nf_conntrack_irc       13348  1 nf_nat_irc
nf_nat_ftp             10880  0 
nf_nat                 25368  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      21900  6 nf_nat
nf_conntrack_ftp       15652  1 nf_nat_ftp
nf_conntrack           72032  8 xt_state,xt_conntrack,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         10752  1 
ip_tables              19600  1 iptable_filter
x_tables               22916  8 ipt_LOG,xt_limit,ipt_addrtype,xt_state,xt_tcpudp,xt_conntrack,ip6_tables,ip_tables
coretemp               14080  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         381488  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
rfkill                 17176  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lbm_cw_mac80211       210728  0 
led_class              12164  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
snd_timer              29960  2 snd_pcm,snd_seq
container              11520  0 
video                  25104  0 
lbm_cw_cfg80211        39696  1 lbm_cw_mac80211
evdev                  17696  13 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               58268  1 sdhci
psmouse                45200  0 
intel_agp              33724  1 
output                 11008  1 video
ricoh_mmc              11904  0 
agpgart                42184  3 drm,intel_agp
pcspkr                 10624  0 
serio_raw              13444  0 
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
battery                18436  0 
ac                     12292  0 
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
ata_generic            12932  0 
sg                     39732  2 
pata_acpi              12160  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  0 
ahci                   37132  4 
ohci1394               37936  0 
libata                177312  4 ata_generic,pata_acpi,ata_piix,ahci
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
e100                   41356  0 
mii                    13440  1 e100
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  5 btusb,usbhid,ehci_hcd,uhci_hcd
dock                   16656  1 libata
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fuse                   60828  3 
vesafb                 13828  1 
fbcon                  47648  72 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


dmesg output attached with this post

hisham@Hisham-NB:~$  sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:c5:6a:85
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=10.8.48.136 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:e9:42:a3:f1:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

hisham@Hisham-NB:~$  iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

hisham@Hisham-NB:~$ lsb_release -d
Description:	Ubuntu 8.10

hisham@Hisham-NB:~$  uname -mr
2.6.27-7-generic i686

hisham@Hisham-NB:~$  sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.

Thanks

---

