---
title: "strange wireless hp laptop"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by mdwalter on 2008-04-09
Hello everybody!!!):P
First I'm sorry for my english.
I have the hp dv9410us laptop with ubuntu beta 8.04, With this version I can use ubuntu, but with 7.10 I can't start ubuntu. (I'm new with linux ubuntu)
In the system 8.04 when I go in networking setting I see the wireless connection with out ESSID list, I try put manual my ESSID with ip, subnet mask and gateway but not work.
I post the message of iwconfig, lspi, iwlist scan, ismod, dmesg. I hope some doby can help me...[-o<[-o<[-o<[-o<

**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr : off   Fragment thr=2346 B   
          Encryption key : off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lspi:**
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

**iwlist scan:**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is do




**lsmod:**

Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  2 
libusual               19108  1 usb_storage
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
rfkill_input            5504  0 
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0 
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   118176  0 
serio_raw               7940  0 
rfkill                  8592  435 rfkill_input,b43
uvcvideo               58116  0 
pcspkr                  4224  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
mac80211              165652  1 b43
psmouse                40336  0 
cfg80211               15112  1 mac80211
evdev                  13056  30 
led_class               6020  1 b43
input_polldev           5896  1 b43
sdhci                  19076  0 
ricoh_mmc               4352  0 
snd_hda_intel         344088  2 
mmc_core               51460  1 sdhci
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
video                  20112  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi_acer                9644  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                14212  0 
ac                      6916  0 
button                  9232  0 
soundcore               8800  1 snd
i2c_nforce2             7680  0 
agpgart                34760  0 
k8temp                  6656  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_core               24832  1 i2c_nforce2
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
amd74xx                10000  0 [permanent]
sd_mod                 30720  6 
ide_core              113996  1 amd74xx
pata_acpi               8320  0 
pata_amd               14212  0 
sata_nv                27528  2 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  4 pata_acpi,pata_amd,sata_nv,ata_generic
ehci_hcd               37516  0 
forcedeth              51980  0 
scsi_mod              151436  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
ohci_hcd               25348  0 
usbcore               146028  6 usb_storage,libusual,uvcvideo,ehci_hcd,ohci_hcd
ssb                    32772  1 b43
thermal                16796  0 
processor              36872  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 





**dmesg:**

[19640.640947] evdev: no more free evdev devices
[19640.640953] input: failed to attach handler evdev to device input378, error: -23
[19640.658278] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19640.658284] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19646.511311] input: b43-phy0 as /devices/virtual/input/input379
[19646.518678] evdev: no more free evdev devices
[19646.518682] input: failed to attach handler evdev to device input379, error: -23
[19646.539894] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19646.539901] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19650.981729] input: b43-phy0 as /devices/virtual/input/input380
[19650.992717] evdev: no more free evdev devices
[19650.992722] input: failed to attach handler evdev to device input380, error: -23
[19651.010859] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19651.010866] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19656.862228] input: b43-phy0 as /devices/virtual/input/input381
[19656.874014] evdev: no more free evdev devices
[19656.874021] input: failed to attach handler evdev to device input381, error: -23
[19656.891467] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19656.891473] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19661.333120] input: b43-phy0 as /devices/virtual/input/input382
[19661.342721] evdev: no more free evdev devices
[19661.342727] input: failed to attach handler evdev to device input382, error: -23
[19661.360074] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19661.360081] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19667.216176] input: b43-phy0 as /devices/virtual/input/input383
[19667.225785] evdev: no more free evdev devices
[19667.225792] input: failed to attach handler evdev to device input383, error: -23
[19667.243118] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19667.243126] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19671.683133] input: b43-phy0 as /devices/virtual/input/input384
[19671.692723] evdev: no more free evdev devices
[19671.692730] input: failed to attach handler evdev to device input384, error: -23
[19671.710269] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19671.710276] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19677.565792] input: b43-phy0 as /devices/virtual/input/input385
[19677.575786] evdev: no more free evdev devices
[19677.575793] input: failed to attach handler evdev to device input385, error: -23
[19677.593134] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19677.593140] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19726.451546] input: b43-phy0 as /devices/virtual/input/input386
[19726.461539] evdev: no more free evdev devices
[19726.461547] input: failed to attach handler evdev to device input386, error: -23
[19726.478885] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19726.478892] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19732.334790] input: b43-phy0 as /devices/virtual/input/input387
[19732.344606] evdev: no more free evdev devices
[19732.344614] input: failed to attach handler evdev to device input387, error: -23
[19732.362059] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19732.362065] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19781.575111] input: b43-phy0 as /devices/virtual/input/input388
[19781.584850] evdev: no more free evdev devices
[19781.584857] input: failed to attach handler evdev to device input388, error: -23
[19781.602231] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19781.602238] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19787.458006] input: b43-phy0 as /devices/virtual/input/input389
[19787.469697] evdev: no more free evdev devices
[19787.469703] input: failed to attach handler evdev to device input389, error: -23
[19787.487132] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19787.487138] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19836.344828] input: b43-phy0 as /devices/virtual/input/input390
[19836.359392] evdev: no more free evdev devices
[19836.359399] input: failed to attach handler evdev to device input390, error: -23
[19836.374645] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19836.374652] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19842.228929] input: b43-phy0 as /devices/virtual/input/input391
[19842.236746] evdev: no more free evdev devices
[19842.236753] input: failed to attach handler evdev to device input391, error: -23
[19842.257655] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19842.257662] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19891.116118] input: b43-phy0 as /devices/virtual/input/input392
[19891.126057] evdev: no more free evdev devices
[19891.126064] input: failed to attach handler evdev to device input392, error: -23
[19891.143427] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19891.143433] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19896.999233] input: b43-phy0 as /devices/virtual/input/input393
[19897.009118] evdev: no more free evdev devices
[19897.009124] input: failed to attach handler evdev to device input393, error: -23
[19897.026469] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19897.026476] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19946.595413] input: b43-phy0 as /devices/virtual/input/input394
[19946.604970] evdev: no more free evdev devices
[19946.604977] input: failed to attach handler evdev to device input394, error: -23
[19946.622319] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19946.622326] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[19952.478496] input: b43-phy0 as /devices/virtual/input/input395
[19952.488034] evdev: no more free evdev devices
[19952.488041] input: failed to attach handler evdev to device input395, error: -23
[19952.505352] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[19952.505359] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20001.363846] input: b43-phy0 as /devices/virtual/input/input396
[20001.373795] evdev: no more free evdev devices
[20001.373802] input: failed to attach handler evdev to device input396, error: -23
[20001.391116] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20001.391123] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20007.247095] input: b43-phy0 as /devices/virtual/input/input397
[20007.256860] evdev: no more free evdev devices
[20007.256867] input: failed to attach handler evdev to device input397, error: -23
[20007.274182] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20007.274189] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20056.132451] input: b43-phy0 as /devices/virtual/input/input398
[20056.142620] evdev: no more free evdev devices
[20056.142627] input: failed to attach handler evdev to device input398, error: -23
[20056.159967] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20056.159974] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20062.016170] input: b43-phy0 as /devices/virtual/input/input399
[20062.023919] evdev: no more free evdev devices
[20062.023926] input: failed to attach handler evdev to device input399, error: -23
[20062.041224] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20062.041230] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20110.901746] input: b43-phy0 as /devices/virtual/input/input400
[20110.909671] evdev: no more free evdev devices
[20110.909679] input: failed to attach handler evdev to device input400, error: -23
[20110.926983] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20110.926989] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20116.783743] input: b43-phy0 as /devices/virtual/input/input401
[20116.790950] evdev: no more free evdev devices
[20116.790954] input: failed to attach handler evdev to device input401, error: -23
[20116.811854] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20116.811861] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20130.086222] usb 2-7: new high speed USB device using ehci_hcd and address 4
[20130.150152] usb 2-7: configuration #1 chosen from 1 choice
[20130.220333] usbcore: registered new interface driver libusual
[20130.236291] Initializing USB Mass Storage driver...
[20130.236800] scsi4 : SCSI emulation for USB Mass Storage devices
[20130.237305] usbcore: registered new interface driver usb-storage
[20130.237309] USB Mass Storage support registered.
[20130.238209] usb-storage: device found at 4
[20130.238212] usb-storage: waiting for device to settle before scanning
[20132.905813] usb-storage: device scan complete
[20132.913173] scsi 4:0:0:0: Direct-Access     SAMSUNG  HM060II          YB20 PQ: 0 ANSI: 4
[20133.364788] sd 4:0:0:0: [sdb] 117304992 512-byte hardware sectors (60060 MB)
[20133.365783] sd 4:0:0:0: [sdb] Write Protect is off
[20133.365788] sd 4:0:0:0: [sdb] Mode Sense: 11 00 00 00
[20133.365790] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[20133.368532] sd 4:0:0:0: [sdb] 117304992 512-byte hardware sectors (60060 MB)
[20133.369780] sd 4:0:0:0: [sdb] Write Protect is off
[20133.369783] sd 4:0:0:0: [sdb] Mode Sense: 11 00 00 00
[20133.369785] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[20133.369790]  sdb: sdb1 sdb2
[20133.377493] sd 4:0:0:0: [sdb] Attached SCSI disk
[20133.377537] sd 4:0:0:0: Attached scsi generic sg2 type 0
[20173.635570] input: b43-phy0 as /devices/virtual/input/input402
[20173.646376] evdev: no more free evdev devices
[20173.646380] input: failed to attach handler evdev to device input402, error: -23
[20173.697604] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20173.697611] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20180.501816] input: b43-phy0 as /devices/virtual/input/input403
[20180.511370] evdev: no more free evdev devices
[20180.511376] input: failed to attach handler evdev to device input403, error: -23
[20180.528745] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20180.528752] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20183.325158] usb 2-7: USB disconnect, address 4
[20183.325497] Buffer I/O error on device sdb2, logical block 14424
[20183.325503] lost page write due to I/O error on sdb2
[20183.325506] Buffer I/O error on device sdb2, logical block 14425
[20183.325508] lost page write due to I/O error on sdb2
[20220.417342] usb 2-7: new high speed USB device using ehci_hcd and address 6
[20220.482967] usb 2-7: configuration #1 chosen from 1 choice
[20220.484907] scsi5 : SCSI emulation for USB Mass Storage devices
[20220.484971] usb-storage: device found at 6
[20220.484974] usb-storage: waiting for device to settle before scanning
[20222.706115] usb-storage: device scan complete
[20222.706614] scsi 5:0:0:0: Direct-Access     SAMSUNG  HM060II          YB20 PQ: 0 ANSI: 4
[20222.927759] sd 5:0:0:0: [sdb] 117304992 512-byte hardware sectors (60060 MB)
[20222.928200] sd 5:0:0:0: [sdb] Write Protect is off
[20222.928204] sd 5:0:0:0: [sdb] Mode Sense: 11 00 00 00
[20222.928206] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[20222.929089] sd 5:0:0:0: [sdb] 117304992 512-byte hardware sectors (60060 MB)
[20222.929535] sd 5:0:0:0: [sdb] Write Protect is off
[20222.929537] sd 5:0:0:0: [sdb] Mode Sense: 11 00 00 00
[20222.929539] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[20222.929543]  sdb: sdb1 sdb2
[20222.932739] sd 5:0:0:0: [sdb] Attached SCSI disk
[20222.932780] sd 5:0:0:0: Attached scsi generic sg2 type 0
[20232.223225] input: b43-phy0 as /devices/virtual/input/input404
[20232.231011] evdev: no more free evdev devices
[20232.231019] input: failed to attach handler evdev to device input404, error: -23
[20232.248432] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20232.248442] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20238.111557] input: b43-phy0 as /devices/virtual/input/input405
[20238.121188] evdev: no more free evdev devices
[20238.121197] input: failed to attach handler evdev to device input405, error: -23
[20238.138880] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20238.138888] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20289.689328] input: b43-phy0 as /devices/virtual/input/input406
[20289.696840] evdev: no more free evdev devices
[20289.696850] input: failed to attach handler evdev to device input406, error: -23
[20289.717789] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20289.717797] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20295.691736] input: b43-phy0 as /devices/virtual/input/input407
[20295.695405] evdev: no more free evdev devices
[20295.695414] input: failed to attach handler evdev to device input407, error: -23
[20295.716420] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20295.716428] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20346.164175] input: b43-phy0 as /devices/virtual/input/input408
[20346.171929] evdev: no more free evdev devices
[20346.171938] input: failed to attach handler evdev to device input408, error: -23
[20346.189307] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20346.189314] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20352.517543] input: b43-phy0 as /devices/virtual/input/input409
[20352.521642] evdev: no more free evdev devices
[20352.521652] input: failed to attach handler evdev to device input409, error: -23
[20352.542600] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20352.542607] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20388.812119] usb 2-7: USB disconnect, address 6
[20401.924891] input: b43-phy0 as /devices/virtual/input/input410
[20401.934422] evdev: no more free evdev devices
[20401.934429] input: failed to attach handler evdev to device input410, error: -23
[20401.951839] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20401.951846] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20407.923202] input: b43-phy0 as /devices/virtual/input/input411
[20407.932980] evdev: no more free evdev devices
[20407.932986] input: failed to attach handler evdev to device input411, error: -23
[20407.950368] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20407.950374] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20419.993141] usb 2-7: new high speed USB device using ehci_hcd and address 8
[20420.057085] usb 2-7: configuration #1 chosen from 1 choice
[20420.064783] scsi6 : SCSI emulation for USB Mass Storage devices
[20420.069583] usb-storage: device found at 8
[20420.069588] usb-storage: waiting for device to settle before scanning
[20422.292553] usb-storage: device scan complete
[20422.293495] scsi 6:0:0:0: Direct-Access     SAMSUNG  HM060II          YB20 PQ: 0 ANSI: 4
[20422.487710] sd 6:0:0:0: [sdb] 117304992 512-byte hardware sectors (60060 MB)
[20422.488039] sd 6:0:0:0: [sdb] Write Protect is off
[20422.488043] sd 6:0:0:0: [sdb] Mode Sense: 11 00 00 00
[20422.488046] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[20422.489039] sd 6:0:0:0: [sdb] 117304992 512-byte hardware sectors (60060 MB)
[20422.489482] sd 6:0:0:0: [sdb] Write Protect is off
[20422.489486] sd 6:0:0:0: [sdb] Mode Sense: 11 00 00 00
[20422.489489] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[20422.489494]  sdb: sdb1 sdb2
[20422.492680] sd 6:0:0:0: [sdb] Attached SCSI disk
[20422.492757] sd 6:0:0:0: Attached scsi generic sg2 type 0
[20462.794002] input: b43-phy0 as /devices/virtual/input/input412
[20462.803685] evdev: no more free evdev devices
[20462.803692] input: failed to attach handler evdev to device input412, error: -23
[20462.821032] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20462.821039] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20468.792323] input: b43-phy0 as /devices/virtual/input/input413
[20468.802215] evdev: no more free evdev devices
[20468.802222] input: failed to attach handler evdev to device input413, error: -23
[20468.819716] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20468.819722] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20517.563532] input: b43-phy0 as /devices/virtual/input/input414
[20517.572510] evdev: no more free evdev devices
[20517.572517] input: failed to attach handler evdev to device input414, error: -23
[20517.589989] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20517.589995] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20525.265305] input: b43-phy0 as /devices/virtual/input/input415
[20525.274836] evdev: no more free evdev devices
[20525.274844] input: failed to attach handler evdev to device input415, error: -23
[20525.292241] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20525.292251] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20576.095057] input: b43-phy0 as /devices/virtual/input/input416
[20576.104174] evdev: no more free evdev devices
[20576.104181] input: failed to attach handler evdev to device input416, error: -23
[20576.121677] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20576.121682] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20582.093184] input: b43-phy0 as /devices/virtual/input/input417
[20582.102733] evdev: no more free evdev devices
[20582.102740] input: failed to attach handler evdev to device input417, error: -23
[20582.120151] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20582.120158] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20632.211942] input: b43-phy0 as /devices/virtual/input/input418
[20632.219663] evdev: no more free evdev devices
[20632.219672] input: failed to attach handler evdev to device input418, error: -23
[20632.237077] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20632.237083] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20638.214008] input: b43-phy0 as /devices/virtual/input/input419
[20638.221777] evdev: no more free evdev devices
[20638.221787] input: failed to attach handler evdev to device input419, error: -23
[20638.239133] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20638.239141] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20686.978330] input: b43-phy0 as /devices/virtual/input/input420
[20686.992043] evdev: no more free evdev devices
[20686.992048] input: failed to attach handler evdev to device input420, error: -23
[20687.007912] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20687.007918] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20692.980773] input: b43-phy0 as /devices/virtual/input/input421
[20692.990603] evdev: no more free evdev devices
[20692.990610] input: failed to attach handler evdev to device input421, error: -23
[20693.008046] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20693.008052] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20744.589090] input: b43-phy0 as /devices/virtual/input/input422
[20744.596373] evdev: no more free evdev devices
[20744.596380] input: failed to attach handler evdev to device input422, error: -23
[20744.617365] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20744.617372] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20751.583188] input: b43-phy0 as /devices/virtual/input/input423
[20751.592193] evdev: no more free evdev devices
[20751.592200] input: failed to attach handler evdev to device input423, error: -23
[20751.609583] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20751.609589] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20802.465032] input: b43-phy0 as /devices/virtual/input/input424
[20802.472454] evdev: no more free evdev devices
[20802.472461] input: failed to attach handler evdev to device input424, error: -23
[20802.493412] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20802.493419] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20808.338868] input: b43-phy0 as /devices/virtual/input/input425
[20808.346636] evdev: no more free evdev devices
[20808.346643] input: failed to attach handler evdev to device input425, error: -23
[20808.367579] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20808.367586] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20857.235671] input: b43-phy0 as /devices/virtual/input/input426
[20857.243065] evdev: no more free evdev devices
[20857.243071] input: failed to attach handler evdev to device input426, error: -23
[20857.265803] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20857.265810] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20863.109982] input: b43-phy0 as /devices/virtual/input/input427
[20863.117247] evdev: no more free evdev devices
[20863.117253] input: failed to attach handler evdev to device input427, error: -23
[20863.138205] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20863.138212] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20912.007911] input: b43-phy0 as /devices/virtual/input/input428
[20912.015441] evdev: no more free evdev devices
[20912.015448] input: failed to attach handler evdev to device input428, error: -23
[20912.036403] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20912.036410] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20917.880063] input: b43-phy0 as /devices/virtual/input/input429
[20917.884295] evdev: no more free evdev devices
[20917.884301] input: failed to attach handler evdev to device input429, error: -23
[20917.908765] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20917.908772] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20969.974758] input: b43-phy0 as /devices/virtual/input/input430
[20969.980142] evdev: no more free evdev devices
[20969.980150] input: failed to attach handler evdev to device input430, error: -23
[20970.004924] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20970.004931] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[20976.655132] input: b43-phy0 as /devices/virtual/input/input431
[20976.675230] evdev: no more free evdev devices
[20976.675238] input: failed to attach handler evdev to device input431, error: -23
[20976.712691] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found or load failed.
[20976.712698] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).

In my desktop pc I buy all item compatible wih linux and wireless too, with this computer(desktop) no problem, all is very nice, but with the laptop....too much problem!!!!!!](*,)
Thank you!!!!

---

