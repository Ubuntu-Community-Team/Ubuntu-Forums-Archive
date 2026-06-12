---
title: "Ubuntu 10.04 -- no wireless connection"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by amudman on 2010-05-02
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
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Chux"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:3
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chuck@chuck-t23laptop:~$ 








__________________

---

### Post by lkraemer on 2010-05-02
Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Please post the output of each command........


lk

---

### Post by chili555 on 2010-05-02
> **lkraemer said:**
> Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Please post the output of each command........


lk

Did you not see his lspci, lsusb and iwconfig already? His wireless is obviously eth1.

---

### Post by chili555 on 2010-05-02
amudman -

You have a wireless interface, eth1. Does Network Manager not see networks? What do these commands tell us?```
sudo iwlist eth1 scan
rfkill list
```Is this, by any chance a Thinkpad T23? If so, please post:```
lsmod | grep -e orin -e host
```Thanks.

---

### Post by amudman on 2010-05-03
Thanks you for your effort, help and concern. I gave up and reformatted back to Ubuntu 9.1. I keep a very active file back up and find many of the problems are more easily and quickly fixed by me by just re-installing.
The laptop is a IBM T23.

I will wait to migrate to the next Ubuntu update to avoid the problems I get into. Ubuntu is a really good system and your help is just simply fantastic.

Problem solved

---

### Post by n0ur on 2010-05-04
Hello people, I have a problem with my wireless too.

Here's what **iwconfig** shows:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
	  Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

pan0      no wireless extensions.

And sudo **iwlist wlan0 scan**:

wlan0     Interface doesn't support scanning : Network is down


And **rfkill list**:

0: dell-wifi: Wireless LAN	
	Soft blocked: no
	Hard blocked: no

1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


Oh and I have a Dell Inspiron 1545 laptop.

All your help is appreciated, thanks for your time : )

---

### Post by xumuk37 on 2010-05-04
```
lspci|grep -i net
```
please

---

### Post by n0ur on 2010-05-04
Hey xumuk37, here's the output of **lspci|grep -i net**

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by xumuk37 on 2010-05-04
```
sudo apt-get update&&sudo apt-get upgrade
sudo aptitude reinstall bcmwl-kernel-source
```and restart

---

### Post by datacrusher on 2010-05-04
I actually lost all my netowork. After trying with no sucess restarting the networkmanager, nd-applet and whatsoever, tryed to reboot on the older kernel 2.6.31 and all worked. 


ill give it a shot before fighting with the new kernel modules.

---

### Post by s.v.z on 2010-05-04
I`ve also got a broadcom BCM card. Had enough trouble with it. If you have a wireless killswitch on your laptop, turn it on and reboot with it turned on already (The bug is that it can only disable wi-fi, not enable it). Saved me a lot of nerves on ubuntu 9.10. Still present in 10.04. If this won`t help, try using not the proprietary Broadcom driver, but the ubuntu wireless STA driver. This worked for me in 10.04. Still, don`t forget about the killswitch ;)

---

### Post by xumuk37 on 2010-05-04
BCM and digits?
what says ```
ifconfig wlan0 up
``` ?

---

### Post by s.v.z on 2010-05-04
Well, it is a Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

---

### Post by xumuk37 on 2010-05-04
n0ur, get the script in attach, do ```
chmod +x wifi.sh
sh wifi.sh
```

---

### Post by xumuk37 on 2010-05-04
s.v.z, try to do same with

---

### Post by sadaruwan12 on 2010-05-04
I had the similar kind of a problem with my rtl8187B wireless what I did is written here try this it might work for you as well

[Click Me]("http://slinuxworld.blogspot.com/2009/11/wifi-problem-solution-for-rtl8187b.html")

---

### Post by amudman on 2010-05-04
Ubuntu 10.04 -- no wireless connection

I am having a horrible time today with my computers! It has been difficult to get my info into the thread but,.... here it is:

I have attached all info asked for and hope for the best. 

Well, I'm stuck in the wireless no-connect after upgrading to 10.04. It(wireless) has worked great , without problems, for several updates. I upgraded with a positive attitude, but I told myself I should wait until others have found and fixed the early problems. I should have waited and I should not have been baited.

I am willing to try and follow anything you offer, if you have the patience.

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
lo no wireless extensions.

eth0 no wireless extensions.

irda0 no wireless extensions.

eth1 IEEE 802.11b ESSID:"Chux" 
Mode:Managed Frequency:2.457 GHz Access Point: None 
Bit Rate:11 Mb/s Sensitivity:1/0 
Retry limit:8 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/70 Signal level=-122 dBm Noise level=-122 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


chuck@chuck-t23laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


chuck@chuck-t23laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

irda0 no wireless extensions.

eth1 IEEE 802.11b ESSID:"Chux" 
Mode:Managed Frequency:2.457 GHz Access Point: None 
Bit Rate:11 Mb/s Sensitivity:1/0 
Retry limit:8 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/70 Signal level=-122 dBm Noise level=-122 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


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
Module Size Used by
michael_mic 1732 4 
orinoco_cs 8782 1 
orinoco 62841 1 orinoco_cs
cfg80211 126485 1 orinoco
btrfs 458906 0 
zlib_deflate 19568 1 btrfs
crc32c 2519 1 
libcrc32c 875 1 btrfs
ufs 72774 0 
qnx4 6484 0 
hfsplus 70800 0 
hfs 40754 0 
minix 25197 0 
ntfs 94791 0 
vfat 8901 0 
msdos 6392 0 
fat 47767 2 vfat,msdos
jfs 172650 0 
xfs 513904 0 
exportfs 3437 1 xfs
reiserfs 225633 0 
isofs 29250 0 
udf 78785 0 
crc_itu_t 1371 1 udf
savage 29488 2 
drm 162471 3 savage
binfmt_misc 6587 1 
snd_intel8x0 25588 2 
snd_ac97_codec 100646 1 snd_intel8x0
ac97_bus 1002 1 snd_ac97_codec
snd_pcm_oss 35308 0 
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70662 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
thinkpad_acpi 68083 0 
snd_seq_dummy 1338 0 
pcmcia 33024 1 orinoco_cs
snd_seq_oss 26726 0 
snd_seq_midi 4557 0 
snd_rawmidi 19056 1 snd_seq_midi
fbcon 35102 71 
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
tileblit 2031 1 fbcon
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
font 7557 1 fbcon
yenta_socket 20408 4 
snd_timer 19098 2 snd_pcm,snd_seq
nsc_ircc 18220 0 
rsrc_nonstatic 10015 1 yenta_socket
bitblit 4707 1 fbcon
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
softcursor 1189 1 bitblit
pcmcia_core 32964 4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd 54148 15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,thinkpad_acpi,snd_seq_oss,snd_rawmidi, snd_seq,snd_timer,snd_seq_device
video 17375 0 
irda 186556 1 nsc_ircc
soundcore 6620 1 snd
vga16fb 11385 1 
led_class 2864 1 thinkpad_acpi
snd_page_alloc 7076 2 snd_intel8x0,snd_pcm
vgastate 8961 1 vga16fb
output 1871 1 video
psmouse 63245 0 
lp 7028 0 
intel_agp 24177 1 
ppdev 5259 0 
crc_ccitt 1339 1 irda
nvram 6171 1 thinkpad_acpi
agpgart 31724 2 drm,intel_agp
parport_pc 25962 1 
shpchp 28820 0 
serio_raw 3978 0 
parport 32635 3 lp,ppdev,parport_pc
e100 28211 0 
mii 4381 1 e100
floppy 53016 0 
chuck@chuck-t23laptop:~$ 


ndiswrapper -1
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile install driver described by 'inffile'
-a devid driver use installed 'driver' for 'devid' (dangerous)
-r driver remove 'driver'
-l list installed drivers
-m write configuration for modprobe
-ma write module alias configuration for all devices
-mi write module install configuration for all devices
-v report version information

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
lo no wireless extensions.

eth0 no wireless extensions.

irda0 no wireless extensions.

eth1 IEEE 802.11b ESSID:"Chux" 
Mode:Managed Frequency:2.457 GHz Access Point: None 
Bit Rate:11 Mb/s Sensitivity:1/0 
Retry limit:8 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/70 Signal level=-122 dBm Noise level=-122 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

chuck@chuck-t23laptop:~$ sudo iwlist eth1 scan
[sudo] password for chuck: 
eth1 Scan completed :
Cell 01 - Address: 00:16:B6:26:13:B4
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=65/70 Signal level=-45 dBm 
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
orinoco_cs 8782 1 
orinoco 62841 1 orinoco_cs
cfg80211 126485 1 orinoco
pcmcia 33024 1 orinoco_cs
pcmcia_core 32964 4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

---

### Post by Old_Grey_Wolf on 2010-05-04
> **n0ur said:**
> Hey xumuk37, here's the output of **lspci|grep -i net**

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I have the same Broadcom BCM4312. Try this command ```
sudo apt-get install b43-fwcutter
``` Then reboot.

---

### Post by pcblues on 2010-05-05
Hi there. 

This worked for me:

If you run this:
sudo lshw -c network

And under the wireless interface it says:
firmware=Lucent/Agere 9.48

Try the following:

WEP worked for me when I renamed /lib/firmware/agere_sta_fw.bin to something else (e.g. agere_sta_fw_bin.old), and then ran:
sudo pccardctl eject; sudo pccardctl insert
which does a reload of the internal card.

When I rebooted again, I had to run sudo pccardctl eject; sudo pccardctl  insert
 again, but YMMV.

Flash/Java can be installed with:
sudo apt-get install ubuntu-restricted-extras
which loads all the good stuff (Java, MS fonts, movie codecs, etc.)
More info here (plus how to install codecs for encrypted DVD playback  etc.)
[http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

Aside from this problem, U10.04 is sweet, even on my old laptop (Dell  C610)


[QUOTE=amudman;9237462]Ubuntu 10.04 -- no wireless connection

I am having a horrible time today with my computers! It has been difficult to get my info into the thread but,.... here it is:

I have attached all info asked for and hope for the best. 

Well, I'm stuck in the wireless no-connect after upgrading to 10.04. It(wireless) has worked great , without problems, for several updates. I upgraded with a positive attitude, but I told myself I should wait until others have found and fixed the early problems. I should have waited and I should not have been baited.

I am willing to try and follow anything you offer, if you have the patience.

Thanks, you all are great to help.

---

### Post by n0ur on 2010-05-06
Hey xumuk37;
I have tried the script you attached, (it removes the B43 and installs sp34152.exe) No errors showed,and it rebooted.
But now my Wicd won't detect the wireless network.
"No wireless networks found"
I am sure it's suppose to show it.

Thanks for your help.

---

### Post by colla on 2010-05-10
Seems that i have the same problem ...
Broadcom and wireless lan on *buntu 
a never ending story 

Since 10.04 i can't autoconnect to any accesspoint 
but if i delete my auto connection and configure it manualy / configure a new autoconnection it works once
until i reboot ...

so actually i have to connect manually each time i use my laptop



> lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
08:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
08:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
08:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

> lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:08:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:08:0d.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:d9:29:d0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:17 ioport:a000(size=256) memory:c0202800-c02028ff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:90:4b:fc:d4:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.109 multicast=yes wireless=IEEE 802.11bg

> lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
ppdev                   5259  0 
snd_hda_codec_si3054     3396  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  5 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
joydev                  8708  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674135  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
b43                   157218  0 
drm                   162471  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd                    54148  21 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              204922  1 b43
ati_agp                 5094  0 
soundcore               6620  1 snd
cfg80211              126485  2 b43,mac80211
fsaa1655g               1482  0 
led_class               2864  1 b43
i2c_piix4               8335  0 
shpchp                 28820  0 
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
k8temp                  3024  0 
agpgart                31724  3 ttm,drm,ati_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
ssb                    37336  1 b43
ieee1394               81181  1 ohci1394
pata_atiixp             3148  4

> cat /etc/modprobe.d/blacklist.conf
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

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"WLAN-723B47"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:4A:00:D7:E7   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by 1Dagars1 on 2010-05-19
Sorry for any confusion i though i was replying in regards to link that was posted to a forum that was said to list out a solution but in reality does not exist. Then, i tried to delete this but cannot. so now i am just apologizing for this post.

---

### Post by 1Dagars1 on 2010-05-22
So I wanted to post a fix i read on a few different threads. Hopefully it will help. I was having problems with an Intersil Corp. ISL3886 [Prism Javelin/Prism xbow] (rev01) so this may not work for all cards. However it did work for mine and hopefully it will work for others that read this thread first before getting too frustrated and reloading 9.x

First connect your machine wired. Using the Synaptic Package Manager download and install "linux-firmware-nonfree 1.8". If it does not show up on your first search go to the Edit menu and select the "Reload Package Information" option. 

After it does its thing you will see "linux-firmware-nonfree 1.8". Mark it for installation, apply and close when done. 

I rebooted at this stage but it may not be required. Unplug the cable and see if your wireless can pick up some networks. if so, try to log in to yours and good luck.

This did work for me and i read this from [launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265") post.

---

### Post by amudman on 2010-05-22
My wireless works great now -- I re-installed 10.04 from a disk image.

I posted my wireless problem several weeks ago. After posting numerous results of tests, nothing worked and I gave up and re-installed 9.4 and my wireless returned. Then my hard drive failed and I downloaded the 10.04 iso, burned a disc, installed and wireless works perfectly--it works with three different wireless cards. Perfecto magico....  Originally, I had upgraded to 10.04 on line during a update session. Maybe it was a bad install or download.

The moral to all of this: I back up all my important files very often. To fix a problem,  I find it is much easier to re-install the operating system on a freshly reformatted drive than fumble around trying to fix something with a bunch of code I don't have a clue of what it means.

Ubuntu installs from a disk are simply the greatest, easy, outstanding and clean. It is so much easier to re-install the system, drag over my files, and be on my way rather than fighting some monster from outer hard drive space. Hard drive space monsters are best fought by the young folks. I am well beyond that category. I'll just re format the rascals.

The good news: Ubuntu 10.04 seems fresh, smooth and happy. I really like it. Good work, folks. Thank you very much for this system.

---

### Post by irv on 2010-05-22
> **amudman said:**
> Thanks you for your effort, help and concern. I gave up and reformatted back to Ubuntu 9.1. I keep a very active file back up and find many of the problems are more easily and quickly fixed by me by just re-installing.
The laptop is a IBM T23.

I will wait to migrate to the next Ubuntu update to avoid the problems I get into. Ubuntu is a really good system and your help is just simply fantastic.

Problem solved

A little advice: I have a Dell 1521 that does not work well with Ubuntu. I got 9.4 to work with it but had to jump through hoops. Ubuntu does not support my wireless card. When 10.04 came out, I downloaded it and ran it from the CD. It did not find my wireless card so I know if I upgraded it would not work also. So the advice I would give to anyone, is try it before you install it. make sure it will work with the live CD.

---

### Post by amudman on 2010-07-01
Well, the wireless problems are a total pain. My Orinoco card will not work with 10.04. It will connect once in a while but fails. It works excellently on windows all the time. In short, it is just not worth the trouble to fumble around with this problem as I do not see a solution presented and prefer Ubuntu over windows. There is a problem. It seems to me to be some kind of conflict. My linksys card works as it should, but I need it for another laptop.

Here is my question: What wireless card(s) is/are "bullet-proof" for Ubuntu?  There is bound to be a brand and specific card that work well and the only thing you have to do is plug the thing int. I will buy a new card to solve this problem. I give up. I am tired of fumbling around trying to solve a problem that appears unsolvable (by me) and waiting for an answer. I use an IBM T23 (have several).

Is there a list of 'plug and play' cards that work and that do not work. Plz show the link, if a list exists. Otherwise, just the make and model of several good wireless cards that will work.

As Clint Eastwood says: go ahead, make my day.  Thanx

---

### Post by irv on 2010-07-02
I don't know if this will help, but here are some that don't seem to work.
[http://ubuntuforums.org/showthread.php?t=1504883]("http://ubuntuforums.org/showthread.php?t=1504883")

And here is     * WifiDocs * WirelessTroubleShootingGuide
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

And I don't know if there is any thing here that could help.
[http://forums.techguy.org/networking/928832-solved-wireless-problem-after-ubuntu.html]("http://forums.techguy.org/networking/928832-solved-wireless-problem-after-ubuntu.html")

Just a few things to try.
Irv

---

### Post by irv on 2010-07-02
I just ran across this thread if you have a xbox 360 with a wireless card.
[http://ubuntuforums.org/showthread.php?t=1522571]("http://ubuntuforums.org/showthread.php?t=1522571")

---

### Post by ZeroFossilFuel on 2010-07-12
I created a new account here just to say THANK YOU! 
Your solution below worked for me.
Dell L400, P-III 700, 256MB RAM, 40GB HD, Lucent Orinoco Gold pc card.
Lucid squeezed onto it from alternate CD. Actually runs pretty decent. 
Now the wireless works too!

Thank you!

Z

> **pcblues said:**
> Hi there. 

This worked for me:

If you run this:
sudo lshw -c network

And under the wireless interface it says:
firmware=Lucent/Agere 9.48

Try the following:

WEP worked for me when I renamed /lib/firmware/agere_sta_fw.bin to something else (e.g. agere_sta_fw_bin.old), and then ran:
sudo pccardctl eject; sudo pccardctl insert
which does a reload of the internal card.

When I rebooted again, I had to run sudo pccardctl eject; sudo pccardctl  insert
 again, but YMMV.

Flash/Java can be installed with:
sudo apt-get install ubuntu-restricted-extras
which loads all the good stuff (Java, MS fonts, movie codecs, etc.)
More info here (plus how to install codecs for encrypted DVD playback  etc.)
[http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

Aside from this problem, U10.04 is sweet, even on my old laptop (Dell  C610)



---

### Post by condamine on 2010-07-15
You may find this post of interest ["Annoying Wireless button bug on Lucid Lynx on Dell Vostro"]("http://ubuntuforums.org/showthread.php?t=1493372") related to rfkill.

My google search on rfkill came up with a couple of useful pages.
[http://www.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6-Beta/html/Power_Management_Guide/RFKill.html"]("http://www.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6-Beta/html/Power_Management_Guide/RFKill.html")
> RFKill is a subsystem in the Linux kernel that provides an interface through which radio transmitters in a computer system can be queried, activated, and deactivated. When transmitters are deactivated, they can be placed in a state where software can reactive them (a soft block) or where software cannot reactive them (a hard block).
[http://wireless.kernel.org/en/users/Documentation/rfkill]("http://wireless.kernel.org/en/users/Documentation/rfkill")
[http://www.mjmwired.net/kernel/Documentation/rfkill.txt]("http://www.mjmwired.net/kernel/Documentation/rfkill.txt")

---

