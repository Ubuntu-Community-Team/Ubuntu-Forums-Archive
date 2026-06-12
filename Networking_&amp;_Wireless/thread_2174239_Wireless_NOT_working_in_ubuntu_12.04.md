---
title: "Wireless NOT working in ubuntu 12.04"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by saurabhsandilya2 on 2013-09-13
I installed Ubuntu 12.04 with Windows 07, and my computer is not detecting any wifi network in ubuntu.
In windows it is working alright, also I had ubuntu 10.04 and 11.04 in both versions wifi was working.
Please have a look at some of the outputs:

(1) lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

(2) sudo lshw -C network
```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:fc:25:a5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=sb v2.17 ip=158.144.54.170 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fc500000-fc50ffff


```

(3) iwlist scan
```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.


```

Thanks in advance!!

---

### Post by praseodym on 2013-09-13
Hi,

you need this firmware package via LAN:

```
sudo apt-get install firmware-b43-lpphy-installer 
```

---

### Post by Hadaka on 2013-09-13
Hi, please show the output of..
```
lspci -n | grep 0280
```

*Note: If...

[14e4:4312] then.
```
sudo apt get install firmware-b43-lpphy-installer
sudo modprobe b43
```
If..
[14e4:4315] then.
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
working now?

---

### Post by saurabhsandilya2 on 2013-09-13
Thanks for showing interest, 
output of lspci -n | grep 0280 is
```
04:00.0 0280: 14e4:4315 (rev 01)
```
and so I tried the second option suggested by you.. 
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
It says:
```
FATAL: Module wl not found.
```

---

### Post by saurabhsandilya2 on 2013-09-13
@Praseodym : Yes I did ... But it's NOT working ... Thanks for showing interest in the problem

---

### Post by Hadaka on 2013-09-13
Hi, please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
boot
thanks

---

### Post by saurabhsandilya2 on 2013-09-13
Hi 
I followed steps suggested by you, but
after ```
sudo apt-get install --reinstall bcmwl-kernel-source
```
It gives an error
```
FATAL: Module wl not found.
```

and pops out error message to report this problem..
and also after ```
sudo modprobe wl
```
It again gives
```
FATAL: Module wl not found.
```

---

### Post by Hadaka on 2013-09-13
ok, try this..
```
sudo apt-get install linux-headers-generic
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
if it doesnt work this time..please post..
```
lsmod
rfkill ist
cat /etc/modules
```
thanks.

---

### Post by saurabhsandilya2 on 2013-09-14
Yes I followed steps suggested by you..this time again after
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
it failed to install it showing the same error message
```
FATAL: Module wl not found.
```

I am posting the outputs suggested by you
(1) lsmod
```
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
i915                  620419  3 
joydev                 17613  0 
drm_kms_helper         49597  1 i915
drm                   287564  4 i915,drm_kms_helper
snd_hda_codec_hdmi     37407  1 
snd_hda_codec_idt      71153  1 
uvcvideo               82214  0 
snd_hda_intel          44339  3 
i2c_algo_bit           13564  1 i915
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
videobuf2_core         40785  1 uvcvideo
r852                   18241  0 
videodev              130053  2 uvcvideo,videobuf2_core
snd_hwdep              13668  1 snd_hda_codec
sm_common              16860  1 r852
nand                   59304  2 r852,sm_common
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
coretemp               13596  0 
mtd                    45243  2 sm_common,nand
nand_ids               12723  1 nand
videobuf2_vmalloc      13056  1 uvcvideo
video                  19652  1 i915
videobuf2_memops       13202  1 videobuf2_vmalloc
psmouse                97873  0 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
nand_bch               13147  1 nand
dell_wmi               12681  0 
serio_raw              13215  0 
sparse_keymap          13890  1 dell_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
bch                    22063  1 nand_bch
lp                     17799  0 
mac_hid                13253  0 
r592                   18144  0 
dell_laptop            17425  0 
snd_timer              29989  2 snd_pcm,snd_seq
nand_ecc               13273  1 nand
memstick               16605  1 r592
dcdbas                 14449  1 dell_laptop
lpc_ich                17144  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
parport                46562  3 parport_pc,ppdev,lp
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 dell_wmi
soundcore              12680  1 snd
microcode              23017  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
firewire_ohci          44864  0 
firewire_core          64836  1 firewire_ohci
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ahci                   25879  2 
libahci                31606  1 ahci
tg3                   165622  0 
ptp                    18668  1 tg3
pps_core               14080  1 ptp
saurabh@saurabh:~$ lsmod
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
i915                  620419  3 
joydev                 17613  0 
drm_kms_helper         49597  1 i915
drm                   287564  4 i915,drm_kms_helper
snd_hda_codec_hdmi     37407  1 
snd_hda_codec_idt      71153  1 
uvcvideo               82214  0 
snd_hda_intel          44339  3 
i2c_algo_bit           13564  1 i915
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
videobuf2_core         40785  1 uvcvideo
r852                   18241  0 
videodev              130053  2 uvcvideo,videobuf2_core
snd_hwdep              13668  1 snd_hda_codec
sm_common              16860  1 r852
nand                   59304  2 r852,sm_common
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
coretemp               13596  0 
mtd                    45243  2 sm_common,nand
nand_ids               12723  1 nand
videobuf2_vmalloc      13056  1 uvcvideo
video                  19652  1 i915
videobuf2_memops       13202  1 videobuf2_vmalloc
psmouse                97873  0 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
nand_bch               13147  1 nand
dell_wmi               12681  0 
serio_raw              13215  0 
sparse_keymap          13890  1 dell_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
bch                    22063  1 nand_bch
lp                     17799  0 
mac_hid                13253  0 
r592                   18144  0 
dell_laptop            17425  0 
snd_timer              29989  2 snd_pcm,snd_seq
nand_ecc               13273  1 nand
memstick               16605  1 r592
dcdbas                 14449  1 dell_laptop
lpc_ich                17144  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
parport                46562  3 parport_pc,ppdev,lp
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 dell_wmi
soundcore              12680  1 snd
microcode              23017  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
firewire_ohci          44864  0 
firewire_core          64836  1 firewire_ohci
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ahci                   25879  2 
libahci                31606  1 ahci
tg3                   165622  0 
ptp                    18668  1 tg3
pps_core               14080  1 ptp

```

(2) rfkill ist
```
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1ubuntu2 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

```

(3) cat /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
```

---

### Post by Hadaka on 2013-09-14
Hi, these commands need to be done from a wired connection
connected to the internet, please do again..while connected..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by saurabhsandilya2 on 2013-09-14
Yes .. I run all the above commands while connected to the internet through wired network..
and my colleagues were suggesting that it is probably a bug in 12.04..
I reinstalled 10.04 and wifi is working there

---

### Post by Hadaka on 2013-09-14
ok, great. Did you do a clean fresh install of 12.04 or an upgrade
type install from 10.04 to 12.04???
next try please do a fresh install of 12.04,then run all the updates
and please post he output of..
```
arch
uname -a
```
then we shall go from there...
thanks.

---

### Post by saurabhsandilya2 on 2013-09-14
Many thanks for taking interest in my problem...
actually I have some busy days ahead...
and I have to install many other softwares So it seems I have to be happy with 10.04 :(
Thank you once again for your efforts

---

### Post by Hadaka on 2013-09-14
ok, be advised..10.04 is no longer suported, which means
you may not be able to use some newer functions and you
also wont get updates for applications and security features.
If you are currently satisfied with the way it is working, please
mark this thread solved.
thanks.

---

### Post by varunendra on 2013-09-15
Hadaka, Saurabh,

The current version of the bcmwl-kernel-source in the default repo. seems to be broken. There is a fixed [newer version]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504") available at launchpad, but it is for 64 bit only (not sure if it'll work with 32 bit or not).
*[COLOR="#FF0000"](**UPDATE:**[/COLOR] The fully working latest versions for both 32 and 64 bits are available in the default (restricted) repository now. Just download the suitable package from [here]("http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/"), and double-click to install)*

However, I believe the b43 should work with this card, with the LP-PHY firmware.

@Saurabh,

If you wish to try 12.04 again, I suggest you install the linux-firmware-nonfree package and try loading b43 -
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rv b43
sudo modprobe -v b43
```
You may have problem with this on a live session because it may have the conflicting module "wl" loaded, which is sometimes hard to remove once in use.

---

### Post by saurabhsandilya2 on 2013-09-15
Hi Varun and Hadaka,
Many thanks for your replies...but I cannot try 12.04 again as I have busy days ahead (starting from monday)
and all the other software (of my interest) installation also takes time.
So I am happy with 10.04..I will try your suggestions later..
(@Hadaka I have marked this thread as solved) might be these information is useful to others.
Thanks again!
with regards
Saurabh

---

### Post by mikepeeters22 on 2013-09-15
> **varunendra said:**
> Hadaka, Saurabh,

The current version of the bcmwl-kernel-source in the default repo. seems to be broken. There is a fixed [newer version]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504") available at launchpad, but it is for 64 bit only (not sure if it'll work with 32 bit or not).

However, I believe the b43 should work with this card, with the LP-PHY firmware.

@Saurabh,

If you wish to try 12.04 again, I suggest you install the linux-firmware-nonfree package and try loading b43 -
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rv b43
sudo modprobe -v b43
```
You may have problem with this on a live session because it may have the conflicting module "wl" loaded, which is sometimes hard to remove once in use.

Thanks updating the broken driver package with the newer one, fixed the problem with the wireless connection on my Lenovo IdeaPad U450p with Broadcom BCM4312.

---

### Post by varunendra on 2013-09-15
> **mikepeeters22 said:**
> Thanks updating the broken driver package with the newer one, fixed the problem with the wireless connection on my Lenovo IdeaPad U450p with Broadcom BCM4312.

Welcome to the forums Mike ! :)

Just to make it clear - I didn't update the package, someone or some team did that. I'm only sharing the info here.

And thanks for the feedback! It helps a lot not only users, but us troubleshooters too - to offer the solution more confidently next time :)

---

### Post by amey2 on 2013-10-15
Thanks hadaka,
this worked for me.:grin: ```
sudo apt-get update

```,

---

