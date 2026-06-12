---
title: "Gusty and 3945"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by dgavenda on 2007-12-08
I am having issues with an Intel 3945 wireless NIC and Gutsy.  Long story very short is it worked with a install of the desktop gutsy but I am having problems with using the alternate version.  

I am using the alternate because I wanted a dual boot.  Anyway, I think I am missing something small (probably config somewhere).  Driving me nuts!!!  I can see wireless networks but can't connect.  I have another laptop w/ same exact card and I can connect using same exact credentials. 

 I think it may have to do w/ wep.



 Here is the usual info:

 lsmod
Module                  Size  Used by
arc4                    2944  0 
ecb                     4608  0 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  0 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
ppdev                  10244  0 
ipv6                  273892  20 
acpi_cpufreq           10568  1 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    19592  0 
container               5504  0 
video                  18060  0 
button                  8976  0 
ac                      6148  0 
battery                11012  0 
dock                   10656  0 
af_packet              24840  8 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
snd_hda_intel         263712  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
ipw3945               119840  1 
snd_seq_oss            33152  0 
uvcvideo               48644  0 
joydev                 11328  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
i2c_core               26112  0 
hci_usb                18332  2 
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
bluetooth              57060  7 rfcomm,l2cap,hci_usb
sky2                   46852  0 
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
sdhci                  18828  0 
mmc_core               28420  1 sdhci
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  0 
agpgart                35016  1 intel_agp
snd                    54660  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ahci                   23300  4 
ata_piix               17540  0 
libata                125168  3 ata_generic,ahci,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               26640  0 
ehci_hcd               36492  0 
usbcore               138632  6 uvcvideo,hci_usb,usbhid,uhci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor



 lspic
-bash: lspic: command not found
dgavenda@dgavenda-laptop:/etc/modprobe.d$ 
dgavenda@dgavenda-laptop:/etc/modprobe.d$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Dan's Network"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:12  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1002   Missed beacon:0



I noticed I get this error:
sudo ifup eth1
Error for wireless request "Set Encode" (8B2A) :


Any ideas?

Thx,

---

