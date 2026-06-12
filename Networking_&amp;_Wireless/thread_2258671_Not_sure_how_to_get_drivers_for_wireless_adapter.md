---
title: "Not sure how to get drivers for wireless adapter"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by justinchen044 on 2014-12-29
Hello, recently I got a wireless adapter ([http://www.netis-systems.com/en/products/Wireless-PCI-Adapters/76.html#.VKG88bAA_M](http://www.netis-systems.com/en/products/Wireless-PCI-Adapters/76.html#.VKG88bAA_M)) for my computer. It worked fine on Windows 8.1 dual boot, but not so on my Ubuntu 14.04 install.
```
sudo lshw -class network
``` outputs:
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 09
       serial: e0:3f:49:b0:c1:e8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbff8000-fbffbfff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:04:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=4 mingnt=2
       resources: memory:febf0000-febfffff

```
I'm not an expert, so I don't know how to install the correct drivers so the "UNCLAIMED" becomes 'claimed'. The one on the manufactor page confuses me.
Anyone could help?

ps: What's Ralink

---

### Post by praseodym on 2014-12-29
Hi,

Ralink is the manufacturer. Please show the outputs of

```
lspci -nnk
lsusb
```
Edit: Does LAN work?

---

### Post by justinchen044 on 2014-12-29
```

lspci -nnk


``` gives:
```

00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge [1022:9600]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8388]
00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
    Kernel driver in use: pcieport
00:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3) [1022:9607]
    Kernel driver in use: pcieport
00:0a.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5) [1022:9609]
    Kernel driver in use: pcieport
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:8389]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Kernel driver in use: ohci-pci
00:12.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller [1002:4398]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Kernel driver in use: ohci-pci
00:13.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller [1002:4398]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 3c)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:8389]
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Kernel driver in use: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:836c]
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Kernel driver in use: ohci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
    Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
    Kernel driver in use: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)
    Subsystem: eVga.com. Corp. Device [3842:3753]
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:3753]
    Kernel driver in use: snd_hda_intel
02:00.0 USB controller [0c03]: ASMedia Technology Inc. Device [1b21:1142]
    Subsystem: ASUSTeK Computer Inc. Device [1043:85bf]
    Kernel driver in use: xhci_hcd
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169
04:06.0 Network controller [0280]: Ralink corp. Device [1814:5362]
    Subsystem: Ralink corp. Device [1814:5362]

```
And ```
lsusb
``````

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 1004:61fe LG Electronics, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 15d9:0a4d Trust International B.V. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
The LG device is the one I'm using as for its usb tethering, if that's what you mean by 'does lan work'

---

### Post by praseodym on 2014-12-29
Ok, there it is:

```
04:06.0 Network controller [0280]: Ralink corp. Device [1814:5362]
    Subsystem: Ralink corp. Device [1814:5362]
```
Install the patched driver for 14.04 for this device via:
```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/19/16/3473742-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched.tar.gz
tar xvf 3473742-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched.tar.gz
cd 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe rt5390sta 
```
Please note that the driver needs to be build again after a kernel upgrade:
```

cd 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched
make clean
make
sudo make uninstall
sudo make install
```
For the LAN device change the driver:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf

```This driver will be build automatically after a kernel upgrade.

Reboot.

---

### Post by justinchen044 on 2014-12-30
Thank you! Worked like a charm
....is what I'd like to say, but now the computer completely freezes when I open a web page. 
Should I reinstall the system?

---

### Post by praseodym on 2014-12-30
Does it freeze with LAN or WLAN?

Edit: I forgot something:
```

wget media.cdn.ubuntu-de.org/forum/attachments/08/18/3473742-RT2860STA.dat.tar.gz
sudo mkdir -p /etc/Wireless/RT2860STA
sudo tar xvf 3473742-RT2860STA.dat.tar.gz -C /etc/Wireless/RT2860STA
```
Reboot.

---

### Post by justinchen044 on 2014-12-31
Wlan
Whole computer would freeze up, can't even get into a tty.

---

### Post by praseodym on 2014-12-31
Tried the edit-commands without opening a webpage first?

---

### Post by justinchen044 on 2014-12-31
Entered it, rebooted, same story.
eh, do you think might be because I was messing around with mod probe without any idea what it does?

---

### Post by praseodym on 2014-12-31
Please run the wireless script again, plus

```
lsmod
lspci -nnk | grep VGA
```

---

### Post by justinchen044 on 2014-12-31
The script output was a bit long, so I put them here > [http://pastebin.com/6u1AG5Ac](http://pastebin.com/6u1AG5Ac)
```
Lsmod
``` gives:
```
Module                  Size  Used by
cdc_ether              14351  0 
usbnet                 43913  1 cdc_ether
cdc_acm                28803  0 
nls_utf8               12557  0 
isofs                  39837  0 
usb_storage            62209  0 
cfg80211              484040  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
snd_hda_codec_hdmi     46368  1 
rt5390sta            1345822  1 
kvm                   455835  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_hda_codec_via      27860  1 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
fam15h_power           13119  0 
snd_rawmidi            30144  1 snd_seq_midi
serio_raw              13462  0 
snd_hwdep              13602  1 snd_hda_codec
edac_core              62291  0 
nouveau              1097199  0 
edac_mce_amd           22617  0 
k10temp                13126  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
sp5100_tco             13979  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
i2c_piix4              22155  0 
mxm_wmi                13021  1 nouveau
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
video                  19476  1 nouveau
ttm                    85150  1 nouveau
drm_kms_helper         55071  1 nouveau
snd                    69322  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   303102  3 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
asus_atk0110           18657  0 
mac_hid                13205  0 
wmi                    19177  2 mxm_wmi,nouveau
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
r8168                 434402  0 
ahci                   25819  2 
r8169                  67581  0 
pata_atiixp            13271  0 
libahci                32716  1 ahci
mii                    13934  2 r8169,usbnet

```
And ```
lspci -nnk | grep VGA
``` Gives
 ```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)

```
All these complicated terms, any resources for learning these?

On a happier note, Happy New Year!

---

### Post by praseodym on 2015-01-01
1) The wrong LAN driver is still loaded:

```
sudo modprobe -rfv r8168 r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

2) This is weird:
```
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```
Change to WPA2-AES (CCMP) in your router, not TKIP!

3) Please install the recommended NVIDIA VGA driver

---

### Post by justinchen044 on 2015-01-01
Nope, did a fresh reinstall and everything.

---

