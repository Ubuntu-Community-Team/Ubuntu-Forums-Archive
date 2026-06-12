---
title: "Atheros AR5006EG on Sony Vaio"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by daz4126 on 2007-10-30
I am pulling my hair out over this.

After doing some searching, it seems that this card should work, but I just cannot get any wifi on my new vaio laptop using Gutsy.

I have the restricted drivers installed. It lists
Atheros Hardware Acces Layer (HAL) as a driver that is in use.

It seems that the card is being noticed but not used from some of the ouputs below, but I am new tto all this and don´t fully understand how it works.

Please could somebody explain if it is possible to get this card to work with a Vaio??

iwconfig gives:

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

lspci -v | grep Ethernet gives

```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

sudo lshw -C network gives:

 ```
 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:80:3d:8e:ee
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.28 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
```




lsmod gives the following output:

```
Module                  Size  Used by
ipv6                  273892  10 
i915                   25856  2 
drm                    83348  3 i915
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
sony_laptop            32088  0 
sonypi                 23960  0 
ppdev                  10244  0 
acpi_cpufreq           10568  2 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
sbs                    19592  0 
battery                11012  0 
video                  18060  162 
container               5504  0 
dock                   10656  0 
button                  8976  0 
ac                      6148  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
pcmcia                 41388  0 
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
ath_pci                98336  0 
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
uvcvideo               48644  0 
wlan                  206660  1 ath_pci
compat_ioctl32          2304  1 uvcvideo
hci_usb                18332  2 
snd_seq_dummy           4740  0 
bluetooth              57060  7 rfcomm,l2cap,hci_usb
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_7xx1               8576  0 
tifm_core              11268  1 tifm_7xx1
ath_hal               192720  1 ath_pci
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
intel_agp              25620  1 
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
agpgart                35016  3 drm,intel_agp
evdev                  11136  9 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  2 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
r8169                  32260  0 
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 uvcvideo,hci_usb,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

Thanks,

DAZ

---

### Post by daz4126 on 2007-10-30
Anyone?

Is there anybody that has figured out this awkward card, or has a clue as to what the problem actually is ... do I need drivers or just to enable the wifi?

cheers,

DAZ

---

### Post by kaervos1024 on 2007-12-14
Hey Daz,

Seems the only way people have been having luck with this particular chipset is by using ndiswrapper...

I noticed a resolution in a different thread: 

[http://ohioloco.ubuntuforums.org/showthread.php?t=621562](http://ohioloco.ubuntuforums.org/showthread.php?t=621562)

The instructions used that resolved the issue were posted by Chalewa, here:

[http://ohioloco.ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ohioloco.ubuntuforums.org/showpost.php?p=3868406&postcount=48)

Good luck!

---

### Post by raiwo on 2007-12-14
are you sure it's  AR5006EG card? > about AR5007EG:Sometimes erroneously reported as an AR5006EG by lspci

check this out & more instructions here: [http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG)

---

### Post by daz4126 on 2008-04-28
Mine is actually the AR5007.

I installed Hardy over the weekend and was disappointed that this card was still not supported out of the box - restricted drivers are installed, but they don't work.

I think the fact that this card is incorrectly identified means that it gets the wrong restricted drivers.

I can get it working with ndiswrapper, but it seems slower to connect than it was on Gutsy. Anybody know how I could get this working natively?

cheers,

DAZ

---

### Post by daz4126 on 2008-04-29
The instructions here worked a treat and now I'm running wifi without ndiswrapper!

[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

Thanks for all the replies everybody!

DAZ

---

