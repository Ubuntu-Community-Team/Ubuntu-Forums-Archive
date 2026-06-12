---
title: "wifi and modem both work but no internet"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by neophyte'or'newbie on 2007-10-01
I am new to ubuntu but not linux and i was hopping configuring this would be a breeze, I should know better by now. Any way I have both my wifi card W54G linksys and 56K modem configured and installed however there I don't get an internet connection and the system will not PING here is are some terminal read outs for iwconfig ifconfig lspci and ismod.  I am your average run of the mill guy who likes to tinker with linux but I do not have a degree in computer science so the more simple the directions the better. Thank you 


creighton@wulgar:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:F4:2B:62   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=74/100  Signal level:-63 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

creighton@wulgar:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:46:89:B4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:CA:46:89:B4  
          inet addr:169.254.8.79  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31486 (30.7 KiB)  TX bytes:31486 (30.7 KiB)

ra1       Link encap:Ethernet  HWaddr 00:1C:10:6A:F1:9E  
          inet6 addr: fe80::21c:10ff:fe6a:f19e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:2 dropped:2 overruns:0 carrier:0
          collisions:19 txqueuelen:1000 
          RX bytes:1858476 (1.7 MiB)  TX bytes:5784 (5.6 KiB)
          Interrupt:20 

creighton@wulgar:~$ lspci |grep -inet
1:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
2:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
3:00:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
4:00:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 05)
5:00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
6:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
7:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
8:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
9:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
10:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
11:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
12:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
13:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
14:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
creighton@wulgar:~$ lsmod
Module                  Size  Used by
ppp_deflate             6912  0 
zlib_deflate           20504  1 ppp_deflate
bsd_comp                7040  0 
ppp_async              13184  0 
ppp_generic            29076  3 ppp_deflate,bsd_comp,ppp_async
slhc                    7680  1 ppp_generic
nls_cp437               6784  1 
isofs                  36284  1 
udf                    85252  0 
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
savage                 34048  2 
ppdev                  10116  0 
drm                    81044  3 savage
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
container               5248  0 
button                  8720  0 
ac                      6020  0 
video                  16388  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
nls_utf8                3072  1 
ntfs                  107764  1 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
snd_via82xx            29208  1 
gameport               16520  1 snd_via82xx
snd_ac97_codec         98336  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
sg                     36252  0 
sd_mod                 23428  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             36388  1 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
via_ircc               27540  0 
parport                36936  3 ppdev,lp,parport_pc
irda                  201276  1 via_ircc
i2c_prosavage           5248  0 
i2c_algo_bit            8712  1 i2c_prosavage
via_agp                11264  1 
pcspkr                  4224  0 
rt61                  245128  1 
crc_ccitt               3072  2 ppp_async,irda
psmouse                38920  0 
serio_raw               7940  0 
snd                    54020  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro             10132  0 
i2c_core               22784  4 i2c_ec,i2c_prosavage,i2c_algo_bit,i2c_viapro
agpgart                35400  2 drm,via_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
soundcore               8672  1 snd
af_packet              23816  4 
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  3 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ide_disk               17024  6 
ata_generic             9092  0 
libata                125720  1 ata_generic
generic                 5124  0 [permanent]
usb_storage            72256  0 
scsi_mod              142348  5 sbp2,sg,sd_mod,libata,usb_storage
libusual               17936  1 usb_storage
floppy                 59524  0 
via82cxxx              10372  0 [permanent]
ehci_hcd               34188  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
uhci_hcd               25360  0 
usbcore               134280  5 usb_storage,libusual,ehci_hcd,uhci_hcd
8139cp                 25088  0 
8139too                27648  0 
mii                     6528  2 8139cp,8139too
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by neophyte'or'newbie on 2007-10-01
forgot to add that I have installed 7.04 Fiesty Fawn

---

