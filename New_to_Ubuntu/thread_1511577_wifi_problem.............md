---
title: "wifi problem............"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by zarac on 2010-06-17
Hi friends,

              i'm using ubuntu 8.04 LTS desktop OS in my lenovo 3000 Y410 lap top. i have installed modules needed for wifi. but LED is not lightening and wifi is not working.
wireless card:    Intel Corporation PRO/Wireless 3945ABG.  expect ur help..             details follows...

sanvish@sanvish-laptop:~$ lspci


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


sanvish@sanvish-laptop:~$ lspci

module                  Size  Used by
af_packet              27272  2
ipv6                  311720  10
i915                   38144  2
drm                   106152  3 i915
rfcomm                 47392  2
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0
acpi_cpufreq           10832  2
cpufreq_userspace       6180  0
cpufreq_stats           8416  0
cpufreq_conservative    10632  0
cpufreq_ondemand       11152  1
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3200  0
dock                   12960  0
sbs                    17808  0
sbshc                   8960  1 sbs
container               6656  0
iptable_filter          4608  0
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
sbp2                   27272  0
parport_pc             41128  0
lp                     14916  0
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0
snd_hda_intel         440408  3
uvcvideo               62084  0
snd_pcm_oss            47648  0
iwl3945               100468  0
snd_mixer_oss          20224  1 snd_pcm_oss
iwlwifi_mac80211      251876  1 iwl3945
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
serio_raw               9092  0
evdev                  14976  8
cfg80211               17680  1 iwlwifi_mac80211
sdhci                  21508  0
mmc_core               59272  1 sdhci
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0
snd_seq_oss            38912  0
ac                      8328  0
snd_seq_midi           10688  0
battery                16776  0
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  23444  0
output                  5632  1 video
snd_timer              27912  2 snd_pcm,snd_seq
pcspkr                  4992  0
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 10912  0
iTCO_wdt               15312  0
iTCO_vendor_support     5764  1 iTCO_wdt
wmi_acer               11076  0
intel_agp              30624  1
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 38172  0
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
psmouse                46236  0
ext3                  149264  2
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0
sr_mod                 20132  0
cdrom                  41512  1 sr_mod
sd_mod                 33280  4
ata_piix               24196  3
ata_generic             9988  0
ohci1394               36532  0
ieee1394              106968  2 sbp2,ohci1394
pata_acpi               9856  0
libata                176304  3 ata_piix,ata_generic,pata_acpi
scsi_mod              178488  5 sbp2,sg,sr_mod,sd_mod,libata
tg3                   124804  0
ehci_hcd               41996  0
uhci_hcd               29856  0
usbcore               169904  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                19744  0
processor              41448  4 acpi_cpufreq,thermal
fan                     6792  0
fbcon                  46336  0
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3


sanvish@sanvish-laptop:~$ sudo lshw -C network

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:a7:82:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s


sanvish@sanvish-laptop:~$ iwconfig wlan0

wlan0     No such device


sanvish@sanvish-laptop:~$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by wintermoon on 2010-06-17
> **zarac said:**
> Hi friends,

              i'm using ubuntu 8.04 LTS desktop OS in my lenovo 3000 Y410 lap top. i have installed modules needed for wifi. but LED is not lightening and wifi is not working.
wireless card:    Intel Corporation PRO/Wireless 3945ABG.  expect ur help..             details follows...

sanvish@sanvish-laptop:~$ lspci


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


sanvish@sanvish-laptop:~$ lspci

module                  Size  Used by
af_packet              27272  2
ipv6                  311720  10
i915                   38144  2
drm                   106152  3 i915
rfcomm                 47392  2
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0
acpi_cpufreq           10832  2
cpufreq_userspace       6180  0
cpufreq_stats           8416  0
cpufreq_conservative    10632  0
cpufreq_ondemand       11152  1
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3200  0
dock                   12960  0
sbs                    17808  0
sbshc                   8960  1 sbs
container               6656  0
iptable_filter          4608  0
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
sbp2                   27272  0
parport_pc             41128  0
lp                     14916  0
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0
snd_hda_intel         440408  3
uvcvideo               62084  0
snd_pcm_oss            47648  0
iwl3945               100468  0
snd_mixer_oss          20224  1 snd_pcm_oss
iwlwifi_mac80211      251876  1 iwl3945
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
serio_raw               9092  0
evdev                  14976  8
cfg80211               17680  1 iwlwifi_mac80211
sdhci                  21508  0
mmc_core               59272  1 sdhci
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0
snd_seq_oss            38912  0
ac                      8328  0
snd_seq_midi           10688  0
battery                16776  0
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  23444  0
output                  5632  1 video
snd_timer              27912  2 snd_pcm,snd_seq
pcspkr                  4992  0
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 10912  0
iTCO_wdt               15312  0
iTCO_vendor_support     5764  1 iTCO_wdt
wmi_acer               11076  0
intel_agp              30624  1
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 38172  0
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
psmouse                46236  0
ext3                  149264  2
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0
sr_mod                 20132  0
cdrom                  41512  1 sr_mod
sd_mod                 33280  4
ata_piix               24196  3
ata_generic             9988  0
ohci1394               36532  0
ieee1394              106968  2 sbp2,ohci1394
pata_acpi               9856  0
libata                176304  3 ata_piix,ata_generic,pata_acpi
scsi_mod              178488  5 sbp2,sg,sr_mod,sd_mod,libata
tg3                   124804  0
ehci_hcd               41996  0
uhci_hcd               29856  0
usbcore               169904  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                19744  0
processor              41448  4 acpi_cpufreq,thermal
fan                     6792  0
fbcon                  46336  0
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3


sanvish@sanvish-laptop:~$ sudo lshw -C network

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:a7:82:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s


sanvish@sanvish-laptop:~$ iwconfig wlan0

wlan0     No such device


sanvish@sanvish-laptop:~$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
You're positive that you installed the *right* drivers? My personal Dell laptop has two wireless drivers available; one works, one doesn't. When in doubt, install all of them (from System - Administration - Hardware Drivers). I personally do not believe in a strict interpretation of "open source" and I'm perfectly fine with a few proprietary drivers.

---

### Post by mapes12 on 2010-06-17
Do you need to turn the device on via your keyboard. Try holding down "Fn" and hitting the "F" key with the wifi symbol on it.

Simple I know, but it's easy to turn off by mistake.

---

### Post by JohnDMcClane on 2010-06-17
When I first started using Ubuntu on my current computer as the only OS (which happened a couple of weeks ago, perhaps a month, but not more), I had problems with the Wi-Fi as well. The only thing that really helped me, was to upgrade it to the latest version of Ubuntu, really. I didn't have a Wi-Fi-option at all, though.

---

### Post by cyberEl on 2010-06-17
i have the same problem on a PackardB easynote laptop with the same wifi card, the kernel drive in use is 
iwl3945, the wifi led goes on but i cannot find the option in Network manager, the wifi card isn't recognized.
i tried with driver update without results too... i also searched the web for some info but what i found did not help me
i am on ubuntu 10.04

---

### Post by ibe2fly4chu on 2010-06-17
read this: [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

then go to [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)

The driver for your wireless card: iwlwifi-3945-ucode-15.32.2.9.tgz
(first one on page). sorry for just posting links...trying  not to die in ffxi as i type xD

---

### Post by cyberEl on 2010-06-17
> **ibe2fly4chu said:**
> read this: [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

then go to [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)

The driver for your wireless card: iwlwifi-3945-ucode-15.32.2.9.tgz
(first one on page). sorry for just posting links...trying  not to die in ffxi as i type xD


thanx for the links, i downloaded the iwlwifi 15.32.2.9 but the instructions on how to install it are not specific for the 10.04, i am quite new in ubuntu and the instructions there dont help me at all....
i dont want to go back to windows in this laptop but wifi is important,
can you help me a bit more?

---

### Post by sadaruwan12 on 2010-06-17
Well I had a Wi-Fi problem with my RTL8187b wireless driver but now it's no more try this workaround.

[Click Here.]("http://openworldlinux.blogspot.com/2010/05/how-to-get-rtl8187b-woring-in-ubuntu.html")

---

