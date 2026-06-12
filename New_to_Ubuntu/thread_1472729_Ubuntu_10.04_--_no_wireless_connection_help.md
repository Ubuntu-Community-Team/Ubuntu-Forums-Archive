---
title: "Ubuntu 10.04 -- no wireless connection help"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by amudman on 2010-05-04
Ubuntu 10.04 -- no wireless connection
Well, I'm stuck in the wireless no-connect after upgrading to 10.04. It(wireless) has worked great , without problems, for several updates. I upgraded with a positive attitude, but I told myself I should wait until others have found and fixed the early problems. I should have waited and I should not have been baited.

The problem is this: I am an not really capable of doing and understanding all the jargon and implementing the wonderful help offered. It often leaves out the info I need to fully follow the suggestions. You, the experts, assume I know all the info you do. Big mistake, but I really try and I really like Ubuntu.

The lack of wireless connectivity(wired works) on my laptop does not seems well understood by all. So, unless someone can help with a fix I propose the best solution for me is to re-install Ubuntu 9.10. I am downloading the file now. What a waste. I am willing to try and follow anything you offer, if you have the patience.

Thanks, you all are great to help.

Chili555 replied:
Re: Problems with wireless connection in Ubuntu 10.04
I will be glad to help. Please start a new thread and open a terminal and post:
Code:
lspci -nn
lsusb
iwconfig
I am confident we can get you going.

wireless fix effort

chuck@chuck-t23laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82830 830 Chipset AGP Bridge [8086:3576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 41)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 01)
01:00.0 VGA compatible controller [0300]: S3 Inc. SuperSavage IX/C SDR [5333:8c2e] (rev 05)
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
02:02.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0449] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 41)
chuck@chuck-t23laptop:~$ 

chuck@chuck-t23laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chuck@chuck-t23laptop:~$ 

chuck@chuck-t23laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

irda0 no wireless extensions.

eth1 IEEE 802.11b ESSID:"Chux" 
Mode:Managed Frequency:2.412 GHz Access Point: None 
Bit Rate:11 Mb/s Sensitivity:1/0 
Retry limit:8 RTS thrff Fragment thrff
Power Managementff
Link Quality=0/70 Signal level=-122 dBm Noise level=-122 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:3
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
[http://ubuntuforums.org/showthread.php?t=1469756](http://ubuntuforums.org/showthread.php?t=1469756)

chuck@chuck-t23laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Chux"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


chuck@chuck-t23laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


chuck@chuck-t23laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Chux"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


chuck@chuck-t23laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)



chuck@chuck-t23laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 41
       serial: 00:d0:59:bf:67:c7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:c0200000-c0200fff ioport:6400(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:9d:e9:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b
chuck@chuck-t23laptop:~$ 



chuck@chuck-t23laptop:~$ lsmod
Module                  Size  Used by
michael_mic             1732  4 
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
cfg80211              126485  1 orinoco
btrfs                 458906  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94791  0 
vfat                    8901  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172650  0 
xfs                   513904  0 
exportfs                3437  1 xfs
reiserfs              225633  0 
isofs                  29250  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
savage                 29488  2 
drm                   162471  3 savage
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
thinkpad_acpi          68083  0 
snd_seq_dummy           1338  0 
pcmcia                 33024  1 orinoco_cs
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
fbcon                  35102  71 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
tileblit                2031  1 fbcon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
font                    7557  1 fbcon
yenta_socket           20408  4 
snd_timer              19098  2 snd_pcm,snd_seq
nsc_ircc               18220  0 
rsrc_nonstatic         10015  1 yenta_socket
bitblit                 4707  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
softcursor              1189  1 bitblit
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd                    54148  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,thinkpad_acpi,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  17375  0 
irda                  186556  1 nsc_ircc
soundcore               6620  1 snd
vga16fb                11385  1 
led_class               2864  1 thinkpad_acpi
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
vgastate                8961  1 vga16fb
output                  1871  1 video
psmouse                63245  0 
lp                      7028  0 
intel_agp              24177  1 
ppdev                   5259  0 
crc_ccitt               1339  1 irda
nvram                   6171  1 thinkpad_acpi
agpgart                31724  2 drm,intel_agp
parport_pc             25962  1 
shpchp                 28820  0 
serio_raw               3978  0 
parport                32635  3 lp,ppdev,parport_pc
e100                   28211  0 
mii                     4381  1 e100
floppy                 53016  0 
chuck@chuck-t23laptop:~$ 


ndiswrapper -1
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
chuck@chuck-t23laptop:~$ 


chuck@chuck-t23laptop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
chuck@chuck-t23laptop:~$ 

chuck@chuck-t23laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Chux"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chuck@chuck-t23laptop:~$ sudo iwlist eth1 scan
[sudo] password for chuck: 
eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:26:13:B4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Chux"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c47d2ba10
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 000443687578
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F5000000

chuck@chuck-t23laptop:~$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

The laptop is an IBM T23
chuck@chuck-t23laptop:~$ lsmod | grep -e orin -e host
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
cfg80211              126485  1 orinoco
pcmcia                 33024  1 orinoco_cs
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

---

### Post by amudman on 2010-05-04
This is a repeat and should be deleted. I have an earlier thread that has this same info.

I am so sorry to create this duplicate, but the problem is still here.

---

