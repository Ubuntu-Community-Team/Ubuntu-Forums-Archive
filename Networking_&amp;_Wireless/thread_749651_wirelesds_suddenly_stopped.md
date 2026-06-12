---
title: "wirelesds suddenly stopped"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by wertyuiop408 on 2008-04-08
Wireless was working fine on my dell inspiron 1525, then it just suddenly stopped, i wasnt rebooting or anything, was just writing some php and i noticed when i tried going to google it said page not found but the icon showed me as still being connected. I tried reconnecting and it did nothing, rebooted and it asked for my wep, typed it in and nothing
Below is the results for lsmod, iwconfig and lshw -C network (were done with a wired connection present)

[HTML]w408@w408-laptop:~$ lsmod
Module                  Size  Used by
snd_rtctimer            4384  0 
binfmt_misc            12936  1 
usbhid                 29536  0 
hid                    28928  1 usbhid
i915                   25856  2 
drm                    83348  3 i915
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
battery                11012  0 
ac                      6148  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
ndiswrapper           193436  0 
bcm43xx               127336  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263840  4 
joydev                 11328  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
sky2                   46852  0 
serio_raw               8068  0 
sdhci                  18828  0 
mmc_core               28420  1 sdhci
psmouse                39952  0 
soundcore               8800  1 snd
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sd_mod                 30336  3 
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ahci                   23300  2 
ata_piix               17540  0 
libata                125168  3 ata_generic,ahci,ata_piix
scsi_mod              147084  5 sbp2,sd_mod,sg,sr_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 usbhid,ndiswrapper,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
w408@w408-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

w408@w408-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3f:39:ce
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.117 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:ca:7b:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.51+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
[/HTML]

---

### Post by R13120(1&lt; on 2008-04-08
the wifi can by tricky and there are alot of different apts that work better for different set ups.
in add remove you might try some different options for apts such as wifi radar and see if you get better results.

---

