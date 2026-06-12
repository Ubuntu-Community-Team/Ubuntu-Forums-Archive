---
title: "Lenovo g40-45 Ubuntu 14.04 Wifi not working"
date: 2015-06-13
forum: Networking &amp; Wireless
---

### Post by lyxcianz on 2015-06-13
Hello, 
I got a Laptop "Lenovo g40 win8" i installed Ubuntu but my Wifi doesnt working.

```
lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1566]
    Subsystem: Lenovo Device [17aa:3801]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon APU E2-4000 with R2 Graphics] [1002:9853]
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:9840]
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: snd_hda_intel
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:156b]
00:02.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
    Kernel driver in use: pcieport
00:02.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
    Kernel driver in use: pcieport
00:08.0 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Device [1022:1537]
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: AMD Cryptographic Coprocessor
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 11)
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801]
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 39)
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 39)
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 42)
    Subsystem: Lenovo Device [17aa:3801]
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 02)
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
    Subsystem: Lenovo Device [17aa:3801]
00:14.7 SD Host controller [0805]: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller [1022:7813] (rev 01)
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: sdhci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1580]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1581]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1582]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1583]
    Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1584]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1585]
01:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3812]
    Kernel driver in use: r8169
```

```
lsusb
Bus 002 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 003: ID 5986:0652 Acer, Inc 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0951:1625 Kingston Technology DataTraveler 101 II
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0951:1665 Kingston Technology 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

```


```
sudo modprobe -v ath9k
insmod /lib/modules/3.16.0-30-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
```

```
rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

Networkmanager doesnt show my Wireless

```
########## wireless info START ##########

Report from: 13 Jun 2015 09:34 PET -0500

Booted last: 13 Jun 2015 04:06 PET -0500

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:45:15 UTC 2015 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3812]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 003: ID 5986:0652 Acer, Inc 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ideapad_laptop         17926  0 
sparse_keymap          13708  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6af7:28ff:fe88:718d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7108539 (7.1 MB)  TX bytes:956640 (956.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search domain.name

##### network managers ##################

Installed:

    NetworkManager

Running:

root       676     1  0 09:06 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             200.48.225.130
    DNS:             200.48.225.146

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Lima (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############
```


```
echo ath9k | sudo tee -a /etc/modules 
ath9k 
```

Reboot without Ethernet

```
lsmod 
Module                  Size  Used by 
nls_iso8859_1          12617  1 
bnep                   18895  2 
rfcomm                 58045  8 
snd_hda_codec_conexant    14400  1 
snd_hda_codec_generic    62873  1 snd_hda_codec_conexant 
snd_hda_codec_hdmi     46396  1 
kvm                   388518  0 
crc32_pclmul           12987  0 
aesni_intel            18170  0 
aes_i586               16995  1 aesni_intel 
xts                    12749  1 aesni_intel 
lrw                    13057  1 aesni_intel 
gf128mul               14503  2 lrw,xts 
ablk_helper            13357  1 aesni_intel 
cryptd                 15578  1 ablk_helper 
parport_pc             32021  0 
ppdev                  17391  0 
ath9k                 122222  0 
ath9k_common           24878  1 ath9k 
joydev                 17113  0 
ath9k_hw              430710  2 ath9k_common,ath9k 
snd_hda_intel          29285  5 
serio_raw              13251  0 
snd_hda_controller     29944  1 snd_hda_intel 
uvcvideo               71465  0 
videobuf2_vmalloc      13048  1 uvcvideo 
snd_hda_codec         120371  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller 
snd_hwdep              13272  1 snd_hda_codec 
videobuf2_memops       13170  1 videobuf2_vmalloc 
rtsx_usb_ms            18249  0 
videobuf2_core         48344  1 uvcvideo 
k10temp                12976  0 
v4l2_common            15132  1 videobuf2_core 
memstick               16174  1 rtsx_usb_ms 
snd_pcm                87194  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller 
ath                    24182  3 ath9k_common,ath9k,ath9k_hw 
videodev              131265  3 uvcvideo,v4l2_common,videobuf2_core 
btusb                  27649  0 
media                  20899  2 uvcvideo,videodev 
mac80211              559049  1 ath9k 
snd_seq_midi           13324  0 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_rawmidi            25722  1 snd_seq_midi 
snd_seq                56592  2 snd_seq_midi_event,snd_seq_midi 
bluetooth             391253  22 bnep,btusb,rfcomm 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi 
radeon               1308261  3 
snd_timer              28648  2 snd_pcm,snd_seq 
6lowpan_iphc           18262  1 bluetooth 
i2c_piix4              17734  0 
cfg80211              418811  4 ath,ath9k_common,ath9k,mac80211 
ttm                    76999  1 radeon 
drm_kms_helper         55007  1 radeon 
snd                    66670  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device 
drm                   255469  6 ttm,drm_kms_helper,radeon 
i2c_algo_bit           13197  1 radeon 
shpchp                 32143  0 
soundcore              14599  2 snd,snd_hda_codec 
ccp                    31128  0 
ideapad_laptop         17926  0 
sparse_keymap          13708  1 ideapad_laptop 
mac_hid                13059  0 
video                  19475  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc 
rtsx_usb_sdmmc         27163  0 
rtsx_usb               20227  2 rtsx_usb_sdmmc,rtsx_usb_ms 
uas                    22631  0 
usb_storage            52721  2 uas 
psmouse                91236  0 
sdhci_pci              18640  0 
r8169                  61579  0 
ahci                   25622  2 
mii                    13654  1 r8169 
sdhci                  38345  1 sdhci_pci 
libahci                26970  1 ahci 



ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 68:f7:28:88:71:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:11263 (11.2 KB)  TX bytes:11263 (11.2 KB) 




 iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 



rfkill list 
0: ideapad_wlan: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: ideapad_bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
2: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 



iwlist chan 
lo        no frequency information. 

eth0      no frequency information. 



sudo iwlist scan 
[sudo] password for ubuntu: 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning.



dmesg | grep ath 
[    1.729551] Loaded X.509 cert 'Magrathea: Glacier signing key: 3c66a93eb5d1a5681166b681a517938d081e4dc7' 
[   16.971721] audit: type=1400 audit(1434227100.721:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=814 comm="apparmor_parser" 

```

still not working

---

### Post by chili555 on 2015-06-14
Except that ath9k isn't correct for your device. I suspect that in a few months (6? 12? More??), the module ath10k_pci will be correct. Please see: [http://lists.infradead.org/pipermail/ath10k/2015-March/004842.html](http://lists.infradead.org/pipermail/ath10k/2015-March/004842.html) and also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)

At this time, we know of no way to get this device working. Sorry.

---

### Post by Pilot6 on 2015-06-15
Why there is no way to use ath10k?

---

### Post by chili555 on 2015-06-15
> **Pilot6 said:**
> Why there is no way to use ath10k?Because:

* Your pci.id of 168c:0041 nor its subsystem aren't yet included in the driver's modaliases, and

* There is no known firmware, and

* The Linux developers have barely begun working on it.

```
$ modinfo ath10k_pci 
filename:       /lib/modules/3.19.0-16-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     5949AF8A9CDDFE454AE281A
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i* [COLOR="#FF0000"] <---no mention of 0041 yet[/COLOR]
depends:        ath10k_core
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

```I suggest you get an inexpensive USB wireless for now and keep checking for your pci.id in Google.

---

### Post by Pilot6 on 2015-06-15
Why don't just add that VID & PID as new_id? It is not a problem at all. Or just add it to source and compile ath10k?
Firmware can be found in a Windows driver.

---

### Post by chili555 on 2015-06-15
> **Pilot6 said:**
> Why don't just add that VID & PID as new_id? It is not a problem at all. Or just add it to source and compile ath10k?
Firmware can be found in a Windows driver.Just because you get a driver to recognize a device and load, doesn't mean that it actually works. If it works at all, it may not work well.

Is this a QCA988X device? Or a QCA6174? Are there some operating differences that need to be accounted for in the driver itself? What needs to be done to get the driver to call up and use the firmware once it's extracted? How do you extract the firmware from Windows? Is the firmware you extract hw2.0 or hw2.1 or hw3.0? How do you get the driver to use it?

If you can solve all these problems, then you are an excellent developer.

---

### Post by Pilot6 on 2015-06-15
I do not now can I solve or not, but somebody has to do it. See that people even do not report the problems to launchpad. In launchpad bugs sit for years.
I fixed some of them and sent upstream. If nobody does it, nothing will ever be fixed.

---

### Post by chili555 on 2015-06-15
> I do not now can I solve or not, but somebody has to do it.Go for it! I will be happy to assist you in any way if I can.

---

### Post by Pilot6 on 2015-06-15
Do you have a device? It is hard to do anything, if noone helps with testing. People just run away as soon as their problem is "solved" for a moment.

---

### Post by Pilot6 on 2015-06-16
This is a new wireless adapter that must be supported by ath10k kernel module.
If you do not have kernel 3.19 yet, then I suggest upgrading it by

    sudo apt-get install linux-generic-lts-vivid

then reboot.

Then I suggest installing the latest linux firmware

Download [https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/linux-firmware_1.144%2Bar3012_all.deb](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/linux-firmware_1.144%2Bar3012_all.deb) to your home folder and run

    sudo dpkg -i linux-firmware*.deb

Then run in terminal

    sudo modprobe ath10k_pci
    echo "168c 0041" | sudo tee /sys/bus/drivers/ath10k_pci/new_id
    sudo modprobe ath10k_pci

This may get wireless to work. If not we will look further.

---

### Post by chili555 on 2015-06-16
I don't believe the "new_id" trick works with PCI devices, only USB.

---

### Post by Pilot6 on 2015-06-16
It works with PCI as well, but Atheros driver may not start correctly. I wlli write it to /etc/modprobe.d then to add new_id.

And it always can be added to source code. But will it work with this adapter or not that is the question.

But this driver is already in stable kernels, that means it works for someone.

---

### Post by chili555 on 2015-06-16
> **Pilot6 said:**
> It works with PCI as well, but Atheros driver may not start correctly. I wlli write it to /etc/modprobe.d then to add new_id.

And it always can be added to source code. But will it work with this adapter or not that is the question.

But this driver is already in stable kernels, that means it works for someone.I will watch with interest.

---

### Post by praseodym on 2015-06-16
Hi,

the problem here is that the firmware is not loaded into the device. See here

[https://forum.ubuntuusers.de/topic/wlan-funktioniert-unter-ubuntu-nicht-unter-win/#post-7396868](https://forum.ubuntuusers.de/topic/wlan-funktioniert-unter-ubuntu-nicht-unter-win/#post-7396868)

and check
```

dmesg | egrep 'firm|ath'
```

We tried compiling it in that thread but it didn't work. Please check also the links on page 3.

---

### Post by mitulsaha on 2015-07-16
Hi. I am having the same problem ... Has anyone able to resolve this?

---

### Post by mitulsaha on 2015-07-16
Hi. Did the wireless got working from there? Thanks.

---

### Post by andibrosig on 2015-10-23
Hi Pilot6,

I have the same problem with my Atheros Wifi card and I would like to offer you my help and my laptop to test your ideas. I know I am a newbie, but I am keen to help crack this problem as I have tried a lot and researched a lot.White listing issues and bios flashing tutorials just don't do it for me.

Andi

---

### Post by jeremy31 on 2015-10-23
This is fixed with [http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in/678244#678244](http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in/678244#678244)

---

