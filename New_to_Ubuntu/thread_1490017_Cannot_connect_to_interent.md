---
title: "Cannot connect to interent"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by 5kTempo on 2010-05-21
First off. Im new to Linux and this is my first real OS experence with it. I just did a custom install of Ubuntu and it looks like it found all of my laptops components. Its an older HP L2000. All is well but I can't connect to the interenet. I can see the wireless icon up on the task bar so I think that is working ok. I click on it to find my connection but nothing appears. On my other computer I can see about 5 other signals but none with Ubuntu. I tried to connect manually but no luck. Also, I have ATT Uverse. Any ideas?

---

### Post by SlidingHorn on 2010-05-21
We'll need more information.  Take a look here for some of the info you could help us by providing: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by 5kTempo on 2010-05-21
Sorry, I know I dont know how to use the grep just yet:




1:
badamez@badamez-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
badamez@badamez-laptop:~$ 



2a:
badamez@badamez-laptop:~$ $ lspci
$: command not found


2b:
badamez@badamez-laptop:~$ lsusb
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 05dc:a782 Lexar Media, Inc. 
Bus 001 Device 012: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 011: ID 04e8:327e Samsung Electronics Co., Ltd 
Bus 001 Device 010: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 009: ID 1532:0012 Razer USA, Ltd 
Bus 001 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
badamez@badamez-laptop:~$ 


3a:
badamez@badamez-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:de:70:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68751 (68.7 KB)  TX bytes:68751 (68.7 KB)

badamez@badamez-laptop:~$ 


3b:
badamez@badamez-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

badamez@badamez-laptop:~$ 


4:
badamez@badamez-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
nls_utf8                1069  0 
isofs                  29250  0 
binfmt_misc             6587  1 
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
ppdev                   5259  0 
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_atiixp             12446  2 
snd_atiixp_modem        9103  0 
joydev                  8708  0 
snd_ac97_codec        100646  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1002  1 snd_ac97_codec
snd_seq_dummy           1338  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_usb_audio          75765  1 
snd_seq_oss            26726  0 
pcmcia                 33024  0 
snd_usb_lib            15658  1 snd_usb_audio
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_pcm                70662  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
radeon                674135  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_hwdep               5412  1 snd_usb_audio
ttm                    49943  1 radeon
b43                   157218  0 
snd_timer              19098  2 snd_pcm,snd_seq
uvcvideo               56990  0 
sdhci_pci               5470  0 
drm_kms_helper         29297  1 radeon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1               3690  0 
mac80211              204922  1 b43
sdhci                  15462  1 sdhci_pci
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
usblp                  10481  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162471  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd                    54148  19 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_hwdep,snd_timer,snd_seq_device
tifm_core               6045  1 tifm_7xx1
cfg80211              126485  2 b43,mac80211
ati_agp                 5094  0 
video                  17375  0 
output                  1871  1 video
led_class               2864  2 b43,sdhci
psmouse                63245  0 
serio_raw               3978  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4               8335  0 
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
pata_atiixp             3148  2 
ieee1394               81181  1 ohci1394
ssb                    37336  1 b43
mii                     4381  2 8139too,8139cp
badamez@badamez-laptop:~$ 



5:

6:  
badamez@badamez-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:de:70:6d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:c0204000-c0205fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:1c:c3:5c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
badamez@badamez-laptop:~$ 


7:  
badamez@badamez-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.

badamez@badamez-laptop:~$ 


8:  
badamez@badamez-laptop:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS
badamez@badamez-laptop:~$ 


8b: 
badamez@badamez-laptop:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
badamez@badamez-laptop:~$ 

9:
badamez@badamez-laptop:~$ uname -mr
2.6.32-21-generic i686
badamez@badamez-laptop:~$ 

10:
badamez@badamez-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
badamez@badamez-laptop:~$

---

### Post by 5kTempo on 2010-05-21
Any ideas?

---

### Post by 5kTempo on 2010-05-22
I figured it out.  I went to Hardware Drivers but since I wasn't  connected to the Internet it couldn't find any problems.  So I directly  connected to my router and the Internet came up fine.  I went back to  Hard Drivers and updated and it found my wireless adapter (Broadcom) and downloaded drivers for it.  I  activated, restarted and it works great now.

---

### Post by quinnten83 on 2010-05-22
yeah broadcom is a b*tch!!!

---

### Post by Kafubie on 2010-05-22
You have BCM 4318...
I have BCM 4312...
I went to this one thread about that could of helped you but it didn't talk about that card. 
Glad you got it working!
:)

---

### Post by ubudog on 2010-05-22
> **quinnten83 said:**
> yeah broadcom is a b*tch!!!

I know, I spent 64.5 hours on it between 8.04 and 9.04.  But in 10.04, the Restricted Drivers work perfectly. Glad you got it fixed and welcome to Ubuntu!

---

