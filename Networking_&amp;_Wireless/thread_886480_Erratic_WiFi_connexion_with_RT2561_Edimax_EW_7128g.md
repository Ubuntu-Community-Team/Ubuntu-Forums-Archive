---
title: "Erratic WiFi connexion with RT2561 Edimax EW 7128g PCI card in Gutsy."
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by 2CV67 on 2008-08-11
Greetings, kind experts!

I have been dual booting Ubuntu/XP on a desktop Acer T120-3000 for 2 years, using an old Atmel USB WiFi adapter.
I just bought a new Edimax EW7128g PCI card with RT2561 chipset to replace the USB device.
This was recommended for Linux, notably Ubuntu 7.10 (up to date) by Linux Emporium & confirmed as suitable for Linux by Edimax - supposedly working “out of the box” without needing to add special drivers.

I installed it in XP with the Ralink driver and it works perfectly all the time, every time, in XP.
It provides much greater signal strength than the old Atmel, judging from the various indicators available in XP.

When I booted to Ubuntu 7.10 (kernel 2.6.22-15) I was very pleased (to put it mildly!) to see it already “found” & identified as wlan1 in Network Settings window (the old USB adapter was wlan0).

I manually configured the connexion with the same SSID, Hexa WEP code & Static I.P. addresses as used by wlan0.
Having activated the connexion, I got Internet straight away, which was very impressive!
So far, so good…

But the connexion appears to come & go erratically even during sessions and half the time Firefox & Evolution fail to get through.
This kind of erratic behaviour never happened with the old Atmel adapter. (It did have other problems, but the connexion never “faded”)

I spent a couple of days trying everything I could think of & everything I could find, but without results.

Attached are the outputs from various relevant commands (I hope!):
cat /etc/lsb-release
lsusb
lspci
lsmod
sudo lshw -C network && route -n
iwconfig
ifconfig
iwlist scan (with & without connexion)
cat /etc/network/interfaces

Can anybody make any sense of all that & point me in the right direction? 	

Thanks in advance!

As a detail:
Is there no signal strength indication in Ubuntu 7.10?
I can see an indication if I select “Roaming” (it shows 75%) but I don’t seem able to establish a connexion at all with Roaming selected.
The indication disappears when Roaming is de-selected.
I would like to add a real-time indicator, like in XP, but have not found one yet.
I tried Wifi Radar which showed the network OK but no signal strength (all grey).
As it seemed to complicate things, I removed it.

:::::::::::::::::::::::::

Terminal output:
chris@DESKTOP:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=7.10 
DISTRIB_CODENAME=gutsy 
DISTRIB_DESCRIPTION="Ubuntu 7.10" 
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ lsusb 
Bus 004 Device 004: ID 045e:0029 Microsoft Corp. IntelliMouse Optical 
Bus 004 Device 003: ID 05e3:0608 Genesys Logic, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1019:0c55  
Bus 001 Device 001: ID 0000:0000  
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge 
00:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI 
00:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01) 
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) 
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge 
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50) 
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01) 
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01) 
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ lsmod 
Module                  Size  Used by 
usblp                  15104  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26112  11 rfcomm 
bluetooth              57060  4 rfcomm,l2cap 
nfsd                  221040  13 
exportfs                7040  1 nfsd 
lockd                  67592  2 nfsd 
sunrpc                172412  8 nfsd,lockd 
ppdev                  10244  0 
radeon                125472  2 
drm                    83348  3 radeon 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand 
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
ac                      6148  0 
battery                11012  0 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
vfat                   14080  2 
fat                    54300  1 vfat 
sbp2                   24072  0 
lp                     12580  0 
ipv6                  273892  10 
snd_via82xx            29336  1 
gameport               16776  1 snd_via82xx 
snd_ac97_codec        100644  1 snd_via82xx 
ac97_bus                3200  1 snd_ac97_codec 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss 
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss 
snd_page_alloc         11400  2 snd_via82xx,snd_pcm 
snd_mpu401_uart         9600  1 snd_via82xx 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi 
sg                     36764  0 
psmouse                39952  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              24324  2 snd_pcm,snd_seq 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc 
sd_mod                 30336  0 
serio_raw               8068  0 
i2c_viapro             10004  0 
pcspkr                  4224  0 
i2c_core               26112  1 i2c_viapro 
snd                    54660  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
arc4                    2944  2 
soundcore               8800  1 snd 
via_ircc               27668  0 
irda                  202300  1 via_ircc 
ecb                     4608  2 
blkcipher               7556  1 ecb 
rc80211_simple          6912  1 
crc_ccitt               3072  1 irda 
rt61pci                24576  0 
rt2x00pci              11520  1 rt61pci 
rt2x00lib              19584  2 rt61pci,rt2x00pci 
rfkill                  8208  1 rt2x00lib 
mac80211              171016  4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib 
cfg80211                7304  1 mac80211 
input_polldev           5896  1 rt2x00lib 
crc_itu_t               3072  1 rt2x00lib 
via_agp                11264  1 
eeprom_93cx6            3200  1 rt61pci 
agpgart                35016  2 drm,via_agp 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp 
af_packet              24840  4 
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3 
mbcache                 9732  1 ext3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd 
ide_disk               18560  5 
ata_generic             8452  0 
libata                125168  1 ata_generic 
usb_storage            73152  0 
scsi_mod              147084  5 sbp2,sg,sd_mod,libata,usb_storage 
usbhid                 29536  0 
hid                    28928  1 usbhid 
libusual               18448  1 usb_storage 
8139too                27776  0 
floppy                 60004  0 
via82cxxx              10372  0 [permanent] 
ide_core              116804  4 ide_cd,ide_disk,usb_storage,via82cxxx 
ehci_hcd               36492  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp 
uhci_hcd               26640  0 
usbcore               138632  7 usblp,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394 
thermal                14344  0 
processor              32072  1 thermal 
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor 
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ sudo lshw -C network && route -n 
[sudo] password for chris: 
  *-network:0             
       description: Wireless interface 
       product: RT2561/RT61 802.11g PCI 
       vendor: RaLink 
       physical id: 8 
       bus info: pci@0000:00:08.0 
       logical name: wmaster0 
       version: 00 
       serial: 00:1f:1f:05:e5:6e 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: e 
       bus info: pci@0000:00:0e.0 
       logical name: eth0 
       version: 10 
       serial: 00:11:5b:00:29:37 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0 
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0 
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan1     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:84:34:15   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:11:5B:00:29:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:18 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:11:5B:00:29:37  
          inet addr:169.254.2.127  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:8505 (8.3 KB)  TX bytes:8505 (8.3 KB) 

wlan1     Link encap:Ethernet  HWaddr 00:1F:1F:05:E5:6E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:67301 (65.7 KB)  TX bytes:61133 (59.7 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-1F-05-E5-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan1     No scan results 
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

BUT ANOTHER TIME

chris@DESKTOP:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan1     Scan completed : 
          Cell 01 - Address: 00:90:4B:84:34:15 
                    ESSID:"DW-B-200-3d555" 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz 
                    Signal level=-68 dBm  
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
                    Extra:tsf=0000000edc22a9cf 

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 

iface eth0 inet dhcp 

auto eth1 
#iface eth1 inet dhcp 

auto eth2 
#iface eth2 inet dhcp 

auto ath0 
#iface ath0 inet dhcp 

iface wlan0 inet static 
#address 192.168.1.9 
#netmask 255.255.255.0 
#gateway 192.168.1.1 
address 192.168.1.9 
netmask 255.255.255.0 
gateway 192.168.1.1 
wireless-key restricted (******correct key hidden********)
wireless-essid DW-B-200-3d555 

auto eth0 

iface wlan1 inet static 
address 192.168.1.9 
netmask 255.255.255.0 
gateway 192.168.1.1 
wireless-key (******correct key hidden********)
wireless-essid DW-B-200-3d555 

auto wlan1 
chris@DESKTOP:~$

---

### Post by 2CV67 on 2008-08-12
Nobody?

---

### Post by 2CV67 on 2008-08-13
Last attempt....

---

### Post by Buster95 on 2008-08-14
No answers really, but I thought that wmaster0 was an internal device and not intended as an external interface. The cut-and-paste below is from a definition.

Is it possible that you've mixed wmaster0 up with wlan0?
Cheers

The master device wmaster0

mac80211 creates creates one master device and as many other secondary devices as requested to represent interfaces for the wireless card you have. mac80211 asks for the master device to appear as named as wmaster%d, and wlan%0 for the interfaces. udev may override the naming convention used though. wmaster%d is an internal master device used only by mac80211. It is currently visible only because it uses netdevice structure which we must allocate and use for for QoS. It also serves as a holder for all interfaces we have, and represent the underlying hardware. For example, when TXing your wlan0 STA interface will actually add IEEE-802.11 header data to a frame with just Ethernet headers, and then pass it down to the master device for actual transmission using the low level drivers.

The wlan%d devices (interfaces) are the devices you would use to configure your wireless settings.

---

### Post by aaronhahn777 on 2009-03-31
I have the very same problem...  with more than one wireless device.  I also used ndiswrapper and a d-link device.

...same problem.

---

### Post by 2CV67 on 2009-04-01
I was advised to upgrade to Hardy, which introduced very frequent kernel panics until I used backports modules to get an updated RT61pci.
Finally I upgraded to Intrepid, which includes a decent driver & I have no more problems.

---

### Post by aaronhahn777 on 2009-04-11
You are using intrepid?  I just re-installed from intrepid to hardy...  it seems to be working "better" than before.  But I still have it drop the signal from time to time (not often).

what driver are you using?

---

### Post by 2CV67 on 2009-04-11
Yes, I have been using Intrepid since 27 January with no problems.

With Intrepid, I use the driver supplied automatically (no backports).

modinfo rt61pci gives me 2.1.8

---

