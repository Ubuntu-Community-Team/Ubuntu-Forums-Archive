---
title: "Help with Ubuntu 7.10 and Dynex DX-WGDTC wireless card"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by hbuch on 2008-04-20
Help with Ubuntu 7.10 and Dynex DX-WGDTC wireless card

Hi. I have just installed Ubuntu 7.10, and I have the Dynex DX-WGDTC wireless card which, unfortunately, doesn't work. I don't have a wired connection, so I'm using a USB key to transfer the troubleshooting information to my Internet-connected laptop. 

Two ideas which come to mind:

I keep hearing about the Broadcom restricted drivers. I can't download anything onto the Ubuntu computer, but I can download onto my other (fedora) computer and transfer stuff via a CD. Is there any place where I can download the broadcom drivers to a non-Ubuntu computer???

Also, would it make sense for me to try to install an older Ubuntu, say 6.06? It seems like the card works well with that version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=293560](http://ubuntuforums.org/showthread.php?t=293560)


Anyway, here is what I did:

Opened System->Administration->Network
set ESSID, pw-type:WEP ascii, entered password, DHCP configuration
set the checkbox. The little telephone tower is blue

Below is the information 
from iwconfig, ifconfig, lspci, lsmod. If anyone can help at all that would be great

Thanks,

Heather Buch

---------------------------


iwconfig results:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"48 plum"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:3242  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---------------------------------------------------

ifconfig results:
ath0      Link encap:Ethernet  HWaddr 00:1A:73:3B:D3:80  
          inet6 addr: fe80::21a:73ff:fe3b:d380/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:1A:73:3B:D3:80  
          inet addr:169.254.7.126  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:A0:CC:D7:4F:7D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:98 dropped:0 overruns:0 carrier:196
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x1000 

eth0:avah Link encap:Ethernet  HWaddr 00:A0:CC:D7:4F:7D  
          inet addr:169.254.8.107  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18912 (18.4 KB)  TX bytes:18912 (18.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1A-73-3B-D3-80-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3341 errors:0 dropped:0 overruns:0 frame:26366
          TX packets:309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:392001 (382.8 KB)  TX bytes:14956 (14.6 KB)
          Interrupt:17 

-----------------------------------------------

lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] System Controller (rev 11)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] AGP Bridge
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] ISA (rev 02)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] IDE (rev 01)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] ACPI (rev 01)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] USB (rev 07)
00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
00:0b.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
00:0d.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
01:05.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82)

---------------------------------------------------------------

lsmod:
Module                  Size  Used by
wlan_wep                8064  1 
ipv6                  273892  10 
mga                    62336  2 
drm                    83348  3 mga
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
ac                      6148  0 
video                  18060  0 
dock                   10656  0 
button                  8976  0 
container               5504  0 
sbs                    19592  0 
battery                11012  0 
lp                     12580  0 
af_packet              24840  6 
snd_usb_audio          81024  0 
snd_usb_lib            17920  1 snd_usb_audio
snd_hwdep              10244  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_ens1371            27680  1 
gameport               16776  1 snd_ens1371
matrox_w1               5120  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            25728  3 snd_usb_lib,snd_ens1371,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wire                   24836  1 matrox_w1
snd_ac97_codec        100644  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
cn                      9632  1 wire
snd_pcm                80388  4 snd_usb_audio,snd_ens1371,snd_ac97_codec,snd_pcm_oss
uvcvideo               48644  0 
snd_timer              24324  2 snd_seq,snd_pcm
wlan_scan_sta          15104  1 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  14 snd_usb_audio,snd_hwdep,snd_seq_oss,snd_ens1371,snd_rawmidi,snd_seq,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_seq_device
ath_rate_sample        14208  1 
shpchp                 34580  0 
compat_ioctl32          2304  1 uvcvideo
pcspkr                  4224  0 
i2c_amd756              7684  0 
snd_page_alloc         11400  1 snd_pcm
pci_hotplug            32704  1 shpchp
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
soundcore               8800  1 snd
cfi_cmdset_0002        24832  8 
cfi_util                4480  1 cfi_cmdset_0002
ath_pci                98336  0 
wlan                  206660  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
psmouse                39952  0 
serio_raw               8068  0 
amd_k7_agp              9868  1 
agpgart                35016  2 drm,amd_k7_agp
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
jedec_probe            17920  0 
cfi_probe               7040  0 
gen_probe               4864  2 jedec_probe,cfi_probe
i2c_core               26112  1 i2c_amd756
amd76xrom               5636  0 
mtd                    17412  10 cfi_cmdset_0002,amd76xrom
chipreg                 4224  3 jedec_probe,cfi_probe,amd76xrom
map_funcs               2944  1 amd76xrom
ath_hal               192720  3 ath_rate_sample,ath_pci
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_disk               18560  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
floppy                 60004  0 
amd74xx                15260  0 [permanent]
ide_core              116804  3 ide_disk,ide_cd,amd74xx
tulip                  53792  0 
ohci_hcd               22916  0 
usbcore               138632  5 snd_usb_audio,snd_usb_lib,uvcvideo,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by hbuch on 2008-04-20
Hi again,

Well, it turns out that the Dynex DX-WGDTC DOES work right out of the box after all! HOORAY!!!

I had managed to confuse my networking by playing with settings too much. 

I finally got things working by backtracking a bit, and with the help of THIS very helpful thread

[http://ubuntuforums.org/showthread.php?t=603154&highlight=broadcom+restricted](http://ubuntuforums.org/showthread.php?t=603154&highlight=broadcom+restricted)

Thanks very much to Gilf! I really look forward to using Ubuntu!

:KS

Heather Buch

---

### Post by rustybronco on 2008-04-22
sorry I didn't see this thread sooner, and could have saved you the heart aches. I have the same card in my desktop and it is one of my cards that never fails me :) the other is my dx-wgnbc in this laptop.
The chipset used in both of them is atheros.
[http://ubuntuhcl.org/browse/product?id=111](http://ubuntuhcl.org/browse/product?id=111)

---

### Post by ejpyle on 2008-05-05
Can anyone send me the INF to get this thing working?
I purchased the DX-WGDTC about 10 months ago at Best Buy and it had no drivers...

I am now staring at my ubuntu box ready to connect though I cant find the INF for this particular card.

The chipset on it says "RT8185L"  

Can anyone hook me up with the drivers?

---

### Post by ejpyle on 2008-05-05
> **ejpyle said:**
> Can anyone send me the INF to get this thing working?
I purchased the DX-WGDTC about 10 months ago at Best Buy and it had no drivers...

I am now staring at my ubuntu box ready to connect though I cant find the INF for this particular card.

The chipset on it says "RT8185L"  

Can anyone hook me up with the drivers?



Never mind I fixed it....man i love Linux... :O)
I used generic RTL8185 drivers....works like a breeze not too mention my wireless connection on Windows was 60% and on UBUNTU it is never lower than 96%.....

Why would that be?

---

