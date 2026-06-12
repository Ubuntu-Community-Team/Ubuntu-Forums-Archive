---
title: "Rosewill Wireless Adapter RNX-250PCe Not Working Ubuntu 13.10"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by TurtleKing on 2014-03-28
I have gone through 4 hours of trouble shooting and googling for solutions to no avail. I feel at this point, I would have better luck getting personalised help, or simply ordering a wireless adapter (hoping to avoid since this one will be sitting around collecting dust).

Please help me find a solution, so I can avoid the cost of getting an optical drive (so I can just put windows back on it).
 My knowledge is in between a Beginner and average user, so please be patient if I ask for extra instructions.

**I will be letting this thread die, as I found a work-aournd (last post). If you have the following combo, I am araid you may end up needing to replace one:**
GIGABYTE A88X FM2+ MOTHERBOARD [B] (mobo seems to be the culprit)
 [/B]ROSEWILL WIRELESS ADAPTER RNX-250PCe
A Linux based OS 64bit (tesed working on Win 7)

---

### Post by pqwoerituytrueiwoq on 2014-03-28
what version of ubuntu are you using? the current version should work with it with 0 effort, just connect to the wifi and you are done

just so you know you can install windows with a usb

edit:
i installed one of those the other week, it just works, the system is using xubuntu 12.10 or 13.10
may have been using a [mainline kernel]("https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater")

make sure the card is showing up as present
```
lspci|egrep -i 'Ethernet|Network|Wifi'
```
if you don't see it in there, you have a hardware issue
edit:
i missed you have 13.10 installed

---

### Post by TurtleKing on 2014-03-28
Ubuntu 13.10 64bit 
I am not even getting the wifi listed, which is why I assume the card has not been configured properly (my phone and windows at least showed it).

I read that I need another computer with a working dvd drive in order to install Windows again (which I don't have).

Could it be my motherboard causing the issue? GIGABYTE FM2+ UP4

---

### Post by Hadaka on 2014-03-28
Hi you have a RTL8192cu chip set in that wireless device.
you need to go to the Real Tec site and download that dirver.
i have little experience with this...but will try to get it going
if you need help.

---

### Post by pqwoerituytrueiwoq on 2014-03-29
i personally know that card works on linux with less effort than a web cam on windows (used a ASrock FM2 microatx motherboard)
the card goes in one of these 3 slots and just works, as long as it is not DOA
[IMG]http://i.imgur.com/HKmL0Lb.png[/IMG]

the usb windows installer [http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool)
since the card is not showing up that will not help you

you may be having a motherboard driver issue
try booting 14.04 beta with a usb and see if it works

---

### Post by TurtleKing on 2014-03-29
Is their terminal info I can provide you folks to see if the card shows up at least?

I know the card still works since I tested it the day before I switched the OS. Also, the card has both lights on which really must be either the motherboard, or the OS not picking it up.

---

### Post by TurtleKing on 2014-03-29
No luck with Ubuntu 14.04 Beta. I tried using the hidden wifi connection feature, but I am getting no signal on all the options I tried. I don't understand why is this motherboard all picky once I switched to Linux (Windows only needed the driver to setup everything).

---

### Post by praseodym on 2014-03-29
Please show the outputs of
```

lspci -nnk
pccardctl info
lsusb
lsmod
rfkill list
cat /etc/resolv.conf
iwconfig
```

---

### Post by TurtleKing on 2014-03-29
Not sure if useful or not, but I found a couple of terminal info commands:

```
familyreyes@home:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1422
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 1423
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1308
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1426
00:03.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1426
00:03.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1426
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141a
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141b
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141c
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141d
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141e
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141f
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)
familyreyes@home:~$ 

```

```
familyreyes@home:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 74:d4:35:08:7f:57  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe08:7f57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:248977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:354806328 (354.8 MB)  TX bytes:11302392 (11.3 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:219102 (219.1 KB)  TX bytes:219102 (219.1 KB)


wlan0     Link encap:Ethernet  HWaddr 68:1c:a2:16:37:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


familyreyes@home:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
familyreyes@home:~$ 




```

```
familyreyes@home:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
familyreyes@home:~$ 

```

```
familyreyes@home:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
snd_hda_codec_realtek    56475  1 
snd_hda_codec_hdmi     41154  1 
joydev                 17377  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
arc4                   12608  2 
snd_seq_midi           13324  0 
microcode              23656  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          52267  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
psmouse                97655  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
serio_raw              13413  0 
k10temp                13126  0 
snd_rawmidi            30095  1 snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_piix4              22106  0 
rtl8192ce              53550  0 
rtl_pci                26641  1 rtl8192ce
rtlwifi                63229  2 rtl_pci,rtl8192ce
rtl8192c_common        49527  1 rtl8192ce
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192ce
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              480503  2 mac80211,rtlwifi
radeon               1408158  2 
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    84169  1 radeon
video                  19318  0 
soundcore              12680  1 snd
drm_kms_helper         52710  1 radeon
drm                   297056  4 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_logitech_dj        18581  0 
hid_generic            12548  0 
usbhid                 53014  0 
usb_storage            62062  0 
hid                   101762  4 hid_generic,usbhid,hid_logitech_dj
ahci                   25819  2 
libahci                32009  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169
familyreyes@home:~$ 



```

```
familyreyes@home:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 74:d4:35:08:7f:57
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:86 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:1c:a2:16:37:31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.11.0-18-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:40 ioport:d000(size=256) memory:fe900000-fe903fff
familyreyes@home:~$ 



```

```
familyreyes@home:~$ iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     No scan results


familyreyes@home:~$ 



```

```
familyreyes@home:~$ sudo iwlist wlan0 scan
wlan0     No scan results


familyreyes@home:~$ 



```

```
familyreyes@home:~$ lsb_release -d
Description:	Ubuntu 13.10
familyreyes@home:~$ 

```
```

familyreyes@home:~$ uname -mr
3.11.0-18-generic x86_64
familyreyes@home:~$ 




```

---

### Post by TurtleKing on 2014-03-29
I have done some of the commands in the post above, but my eyes are too tired to tell, so here are the ones you requested:
```
familyreyes@home:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1422]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1422]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Device [1022:1423]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1423]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [1002:130f]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:0123]
    Kernel driver in use: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:1308]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:0123]
    Kernel driver in use: snd_hda_intel
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1424]
00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1424]
00:03.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1426]
    Kernel driver in use: pcieport
00:03.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1426]
    Kernel driver in use: pcieport
00:03.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:1426]
    Kernel driver in use: pcieport
00:04.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1424]
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: xhci_hcd
00:10.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801] (rev 40)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:b002]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 16)
    Subsystem: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b]
    Kernel driver in use: piix4_smbus
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:a002]
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
    Subsystem: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7809] (rev 11)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:141a]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:141b]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:141c]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:141d]
    Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:141e]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:141f]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178]
    Kernel driver in use: rtl8192ce
03:00.0 USB controller [0c03]: VIA Technologies, Inc. Device [1106:3483] (rev 01)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5007]
familyreyes@home:~$ pccardctl info
familyreyes@home:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1b1c:1b09 Corsair 
Bus 003 Device 002: ID 1b1c:1b05 Corsair 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
familyreyes@home:~$ lsmod
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
snd_hda_codec_realtek    56475  1 
snd_hda_codec_hdmi     41154  1 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
joydev                 17377  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
arc4                   12608  2 
snd_hda_intel          52267  5 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
microcode              23656  0 
snd_rawmidi            30095  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse                97655  0 
serio_raw              13413  0 
k10temp                13126  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
rtl8192ce              53550  0 
i2c_piix4              22106  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
radeon               1408158  2 
rtl_pci                26641  1 rtl8192ce
rtlwifi                63229  2 rtl_pci,rtl8192ce
rtl8192c_common        49527  1 rtl8192ce
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              480503  2 mac80211,rtlwifi
ttm                    84169  1 radeon
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         52710  1 radeon
drm                   297056  4 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
video                  19318  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
hid_logitech_dj        18581  0 
usbhid                 53014  0 
hid                   101762  4 hid_generic,usbhid,hid_logitech_dj
ahci                   25819  2 
libahci                32009  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169
familyreyes@home:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
familyreyes@home:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home
familyreyes@home:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
familyreyes@home:~$ 
```
Off to sleep after this, before I wake up with keyboard marks on my face.

---

### Post by praseodym on 2014-03-29
This device/driver combo is known to cause problems. Try these module parameters first:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

Additionally, update the driver via LAN:
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot.

---

### Post by TurtleKing on 2014-03-29
Still not working. Do you (anyone) remember if you actually had to create the Wifi network? Or did it simply show up as an option under the internet menu?

I am starting to think maybe I am not connecting to the FIOS router properly?

---

### Post by TurtleKing on 2014-03-29
Apparently it is suppose to show right away. I found a work around by installing the card on our family/work PC. Worked as soon as I plugged it inside (asrock am2 mobo). I plugged in a wired connection to the htpc.

I will put a warning in the first post in case someone runs into this bad hardware combo.

Thanks for the effort folks.

---

### Post by pqwoerituytrueiwoq on 2014-03-29
did you check the motherboard for BIOS updates?

---

