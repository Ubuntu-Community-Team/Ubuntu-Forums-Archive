---
title: "Wireless device auto-incrementing"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by vedema on 2007-12-09
Hey guys, I have an odd problem.

I have a wireless card covered under the RaLink drivers, everything works fine, but every time i reboot the wireless device is auto-incremented by 1. As in, on first boot, it was wlan0, on reboot it showed as wlan1, next reboot, wlan2, wlan3, etc. The thing is, it's the same device and hasn't been removed from the PCI slot it resides in. I've went through the config files and I can't find anything wrong, so I'm stumped.

Here's output of lspci and friends:

lspci:

> root@ubuntu:~# lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:0e.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
root@ubuntu:~# 


lsmod:

> root@ubuntu:~# lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
vmnet                  44596  12 
vmblock                16288  3 
vmmon                 945260  0 
binfmt_misc            12936  1 
nfnetlink_queue        13760  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
vboxdrv                60208  0 
nf_conntrack_ipv4      19724  3 
xt_tcpudp               4224  9 
iptable_filter          3968  1 
ip_tables              13924  1 iptable_filter
xt_state                3456  3 
nf_conntrack           65288  2 nf_conntrack_ipv4,xt_state
nfnetlink               6936  4 nfnetlink_queue,nf_conntrack_ipv4,nf_conntrack
xt_NFQUEUE              2944  3 
x_tables               16260  4 xt_tcpudp,ip_tables,xt_state,xt_NFQUEUE
ppdev                  10244  0 
ipv6                  273892  12 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
dock                   10656  0 
sbs                    19592  0 
container               5504  0 
video                  18060  0 
button                  8976  0 
ac                      6148  0 
battery                11012  0 
af_packet              24840  2 
lp                     12580  0 
loop                   19076  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
wm8775                  7180  0 
cx25840                26640  0 
tuner                  63144  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
rt61pci                24576  0 
rt2x00pci              11520  1 rt61pci
rt2x00lib              19584  2 rt61pci,rt2x00pci
snd_seq_midi            9600  0 
rfkill                  8208  1 rt2x00lib
mac80211              171016  4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib
cfg80211                7304  1 mac80211
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
eeprom_93cx6            3200  1 rt61pci
nvidia               6221648  34 
snd_rawmidi            25728  1 snd_seq_midi
lmpcm_usb               7168  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
hci_usb                18332  2 
ivtv                  134928  0 
i2c_algo_bit            7428  1 ivtv
cx2341x                13316  1 ivtv
bluetooth              57060  7 rfcomm,l2cap,hci_usb
tveeprom               16784  1 ivtv
i2c_core               26112  7 wm8775,cx25840,tuner,nvidia,ivtv,i2c_algo_bit,tveeprom
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
videodev               29312  1 ivtv
v4l2_common            18432  6 wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15364  2 ivtv,videodev
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
pcspkr                  4224  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                39952  0 
serio_raw               8068  0 
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usb_storage            73024  1 
ide_core              116804  1 usb_storage
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  6 
usbhid                 29536  0 
ata_generic             8452  0 
hid                    28928  1 usbhid
libusual               18448  1 usb_storage
floppy                 60004  0 
e100                   37644  0 
mii                     6528  1 e100
ehci_hcd               36492  0 
ohci1394               36528  0 
ieee1394               96312  1 ohci1394
ata_piix               17540  4 
libata                125168  2 ata_generic,ata_piix
uhci_hcd               26640  0 
usbcore               138632  8 lmpcm_usb,hci_usb,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
root@ubuntu:~# 


ifconfig:

> wlan5     Link encap:Ethernet  HWaddr 00:0E:3D:09:1A:E5  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:3dff:fe09:1ae5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1441251 (1.3 MB)  TX bytes:241642 (235.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-3D-09-1A-E5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@ubuntu:~# 


---

### Post by vedema on 2007-12-10
anyone have anything on this?

---

