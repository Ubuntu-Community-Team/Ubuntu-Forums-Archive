---
title: "Help with installing ASUS PCE-N53 Wireless network card on Ubuntu 14.04"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by Fong_Wee_Kim on 2014-05-01
Dear all,

I am a new Ubuntu user currently on 14.04 LTS. I just purchased a ASUS PCE-N53 card and is trying to make it work. So far, it has been frustrating and would appreciate some help here.

This is the output from terminal

Code:
uname -a
Linux fong-GA-880GA-UD3H 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge [1022:9601]
    Subsystem: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge [1022:9601]
00:01.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602]
00:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3) [1022:9607]
    Kernel driver in use: pcieport
00:09.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4) [1022:9608]
    Kernel driver in use: pcieport
00:0a.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5) [1022:9609]
    Kernel driver in use: pcieport
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40)
    Subsystem: Gigabyte Technology Co., Ltd GA-MA770-DS3rev2.0 Motherboard [1458:b002]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5002]
    Kernel driver in use: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:a102]
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
    Kernel driver in use: pcieport
00:15.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
    Kernel driver in use: pcieport
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ehci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250] [1002:9715]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
    Kernel driver in use: radeon
01:05.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series] [1002:970f]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:960f]
    Kernel driver in use: snd_hda_intel
02:00.0 Network controller [0280]: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]
    Subsystem: ASUSTeK Computer Inc. Device [1043:851a]
03:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5007]
    Kernel driver in use: xhci_hcd
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
05:0e.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:1000]
    Kernel driver in use: firewire_ohci
06:00.0 SATA controller [0106]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:b000]
    Kernel driver in use: ahci
06:00.1 IDE interface [0101]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:b000]
    Kernel driver in use: pata_jmicron

lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fongweekim@fong-GA-880GA-UD3H:~$ lsmod
Module                  Size  Used by
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
joydev                 17381  0 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
snd_hda_codec_realtek    61438  1 
serio_raw              13462  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
k10temp                13126  0 
snd_hwdep              13602  1 snd_hda_codec
edac_core              62291  0 
snd_rawmidi            30144  1 snd_seq_midi
edac_mce_amd           22617  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
sp5100_tco             13979  0 
i2c_piix4              22155  0 
radeon               1514165  3 
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
soundcore              12680  1 snd
drm                   302817  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
shpchp                 37032  0 
parport_pc             32701  0 
mac_hid                13205  0 
wmi                    19177  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
firewire_ohci          40409  0 
pata_jmicron           12758  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13271  0 
ahci                   25819  2 
libahci                32168  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169

iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


I appreciate all help. Thanks

---

### Post by praseodym on 2014-05-01
Hi,

try this driver:

[http://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915](http://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915)

---

### Post by Fong_Wee_Kim on 2014-05-30
I tried the fix but it hangs the computer. Can anyone help?

---

### Post by praseodym on 2014-05-30
When does it hang? Does it compile?

---

