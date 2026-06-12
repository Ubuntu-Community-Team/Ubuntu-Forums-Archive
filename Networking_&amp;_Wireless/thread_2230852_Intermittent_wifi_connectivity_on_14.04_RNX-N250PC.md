---
title: "Intermittent wifi connectivity on 14.04 RNX-N250PCe"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by freakidz on 2014-06-21
I've tried a few things but the wifi continues to drop intermittently. I'm not sure I have the correct wifi driver installed for my wireless card RNX-N250PCe. I have 2844083-rtl8192ce_dkms_2.6.0006.0321.tar.gz, but am not sure it's installed properly. 


when working: 
```

$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"snappy"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 10:6F:3F:E7:34:5E   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:378   Missed beacon:0




$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:16:7e:22:4b:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88754 (88.7 KB)  TX bytes:88754 (88.7 KB)


wlan0     Link encap:Ethernet  HWaddr 68:1c:a2:16:73:95  
          inet addr:192.168.11.6  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::6a1c:a2ff:fe16:7395/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14015249 (14.0 MB)  TX bytes:2342654 (2.3 MB)

$ nm-tool
NetworkManager Tool


State: connected (global)


- Device: wlan0  [snappy] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        68:1C:A2:16:73:95


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    FBI:             Infra, 00:1A:70:00:55:D1, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA
    Spider's net:    Infra, C0:C1:C0:46:CE:FE, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    wisconsin:       Infra, F8:35:DD:3D:43:9C, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2
    DIRECT-roku-D54040: Infra, B8:3E:59:E5:CA:E1, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2
    pvpad:           Infra, B8:E6:25:9B:1A:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    CRBMRN:          Infra, 90:84:0D:DB:F2:65, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    HOME-9D8A-2.4:   Infra, 54:BE:F7:F4:86:90, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    weasel2.4G:      Infra, 28:C6:8E:0A:00:52, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    xfinitywifi:     Infra, C6:A4:62:FD:FB:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    *snappy:         Infra, 10:6F:3F:E7:34:5E, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    737 Wisconsin:   Infra, C4:3D:C7:89:6D:C6, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WPA
    gatornet:        Infra, 00:22:3F:9B:98:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
    HOME-935F:       Infra, CC:35:40:CB:93:5F, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    wabisabi:        Infra, 90:72:40:15:94:9A, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    DANIELA-RUAH:    Infra, CC:A4:62:FD:FB:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2


  IPv4 Settings:
    Address:         192.168.11.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1


    DNS:             192.168.11.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        40:16:7E:22:4B:C2


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




```


when not working:


```

$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off




$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:16:7e:22:4b:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:236430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16068322 (16.0 MB)  TX bytes:16068322 (16.0 MB)


wlan0     Link encap:Ethernet  HWaddr 68:1c:a2:16:73:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19071401 (19.0 MB)  TX bytes:4438262 (4.4 MB)




$ nm-tool
NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        68:1C:A2:16:73:95


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        40:16:7E:22:4B:C2


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off



```


other info:
```

$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18]
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port E) [1002:5a19]
00:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port G) [1002:5a1b]
00:09.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) [1002:5a1c]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40)
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XTX [Radeon R7 260X] [1002:6658]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:0002]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
04:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)




$ lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
joydev                 17381  0 
arc4                   12608  2 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
video                  19476  1 asus_wmi
mxm_wmi                13021  0 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
snd_hda_codec_realtek    61438  1 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
snd_hda_intel          52355  5 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_seq_midi           13324  0 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
rtl8192ce              53550  0 
snd_rawmidi            30144  1 snd_seq_midi
rtl_pci                26690  1 rtl8192ce
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
rtlwifi                63475  2 rtl_pci,rtl8192ce
radeon               1514165  4 
serio_raw              13462  0 
rtl8192c_common        53172  1 rtl8192ce
k10temp                13126  0 
fam15h_power           13119  0 
edac_core              62291  0 
mac80211              626557  3 rtl_pci,rtlwifi,rtl8192ce
edac_mce_amd           22617  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
sp5100_tco             13979  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
i2c_piix4              22155  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
parport_pc             32701  0 
cfg80211              484040  2 mac80211,rtlwifi
snd_timer              29482  2 snd_pcm,snd_seq
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
ppdev                  17671  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   302817  6 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13205  0 
wmi                    19177  2 mxm_wmi,asus_wmi
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               102222  0 
ahci                   25819  2 
libahci                32168  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169




$ sudo lshw
[...]
           *-network
                description: Wireless interface
                product: RTL8192CE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 68:1c:a2:16:73:95
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=3.13.0-29-generic firmware=N/A ip=192.168.11.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:48 ioport:c000(size=256) memory:fe700000-fe703fff
[...]

```

Any guidance I can get would be great.

---

### Post by squakie on 2014-06-21
Did you install via the software center?

Have you rebooted?

It *might* be that the module needs to be loaded via modprobe.

Please post back the output of:

lsmod

---

### Post by freakidz on 2014-06-21
I tried to install the driver then ended up reinstalling 14.04 due to poor partitioning. I've restarted a few times in the course of troubleshooting. The card can find the network, but has been intermittently dropping. Here's lsmod:

```

$ lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
arc4                   12608  2 
joydev                 17381  0 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
video                  19476  1 asus_wmi
mxm_wmi                13021  0 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_seq_midi           13324  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec_realtek    61438  1 
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            30144  1 snd_seq_midi
radeon               1514165  4 
snd_hda_intel          52355  5 
rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
serio_raw              13462  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtlwifi                63475  2 rtl_pci,rtl8192ce
edac_core              62291  0 
rtl8192c_common        53172  1 rtl8192ce
snd_hwdep              13602  1 snd_hda_codec
edac_mce_amd           22617  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
k10temp                13126  0 
fam15h_power           13119  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mac80211              626557  3 rtl_pci,rtlwifi,rtl8192ce
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
sp5100_tco             13979  0 
snd_timer              29482  2 snd_pcm,snd_seq
i2c_piix4              22155  0 
ttm                    85115  1 radeon
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              484040  2 mac80211,rtlwifi
drm_kms_helper         52758  1 radeon
drm                   302817  6 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
wmi                    19177  2 mxm_wmi,asus_wmi
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               102222  0 
ahci                   25819  2 
libahci                32168  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169

```

---

### Post by freakidz on 2014-06-22
Realized I was vague about how I tried to install the driver -> I downloaded the tar.gz from[ Rosewill's site]("http://www.rosewill.com/support/Support_Download.aspx?ids=3_145_360_1870&flag=d"), make, make install. I have since tried to modprobe, but I don't know what I'm doing so I may have screwed that up. I notice now that the driver says it supports up to kernel 3.2.x and I'm at 3.13.0-29... so is that the issue? Should I install an older version of Ubuntu?

Is it correct that my Rosewill RNX-N250NCe wireless card ([this link ]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRosewill")suggested it is supported, though I now notice the parent of that page doesn't list anything for Rosewill under PCI) is recognized by my computer as a "Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter?"

I ran the wireless script in case I haven't posted enough info:
```

########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux loki 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169


05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178]
    Kernel driver in use: rtl8192ce


##### lsusb #####


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 04f2:0833 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 09da:9066 A4 Tech Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626557  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"snappy"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:366   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 wlan0
192.168.11.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search hsd1.ca.comcast.net


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [snappy] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    FBI:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA
    Spider's net:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    wisconsin:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2
    PS4-78112887AB3C:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    pvpad:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    DANIELA-RUAH:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    gatornet:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
    CRBMRN:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    wabisabi:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    weasel2.4G:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    *snappy:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2
    HOME-935F:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    deOuro_1:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    xfinitywifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    jonandjoy:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    DIRECT-roku-D54040: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2


  IPv4 Settings:
    Address:         192.168.11.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1


    DNS:             192.168.11.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"snappy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a70f3ec77
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0006736E61707079
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD6E0050F204104A0001101044000102103B00010310470010048205192EDC5F339AB1E291D0D112B81021000644442D5752541023000A575A522D36303044485010240001301042000531323334351054000800060050F20400011011000644442D575254100800020104103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"DANIELA-RUAH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000140063a1143
                    Extra: Last beacon: 1708ms ago
                    IE: Unknown: 000C44414E49454C412D52554148
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010030
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880CCA462FDFB40103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030069127A
                    IE: Unknown: DD07000C4303000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001400630c321
                    Extra: Last beacon: 2320ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 05040001006C
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030069127A
                    IE: Unknown: DD07000C4303000000
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"FBI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005db2674a4b
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0003464249
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"PS4-78112887AB3C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f70d05b1d
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00105053342D373831313238383741423343
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C1103FFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000140064cdbbf
                    Extra: Last beacon: 476ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503004C127A
                    IE: Unknown: DD07000C4303000000
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Spider's net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000628942ddd9a
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C5370696465722773206E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B00010310470010E4A82D1136BB72F3ABED2617E57758781021000C4C696E6B73797320496E632E1023000D4C696E6B7379732045323030301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532303030100800020084
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"pvpad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003401d9d028
                    Extra: Last beacon: 384ms ago
                    IE: Unknown: 00057076706164
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"CRBMRN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000182b74c69322
                    Extra: Last beacon: 19628ms ago
                    IE: Unknown: 00064352424D524E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E95
                    IE: Unknown: 3302510B
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301720320
                    IE: Unknown: DD0E0017F2070001010690840DDBF265
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"wisconsin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001396e268e6
                    Extra: Last beacon: 18892ms ago
                    IE: Unknown: 0009776973636F6E73696E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1ABC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD830050F204104A0001101044000102103B000103104700101E9BB04DE8F2E919855DC2F7BCCF4D52102100084D6F746F726F6C61102300084D6F746F726F6C611024000631323334353610420007303030303030311054000800060050F20400011011000A4D6F746F726F6C614150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180208000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


##### iwlist channel #####


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### modinfo #####


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9B7F19319428FF0EFE7E350
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     27E91755814596D634B7709
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512


##### modules #####


lp
rtc


##### blacklist #####


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
blacklist iwlwifi


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    8.707027] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    8.882168] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.882358] rtlwifi: wireless switch is on
[   12.869628] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.869875] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.782737] wlan0: authenticate with <MAC address removed>
[   13.792830] wlan0: send auth to <MAC address removed> (try 1/3)
[   13.807837] wlan0: authenticated
[   13.810123] wlan0: associate with <MAC address removed> (try 1/3)
[   13.814585] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[   13.814711] wlan0: associated
[   13.814756] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   78.953205] wlan0: Connection to AP <MAC address removed> lost
[   80.281512] wlan0: authenticate with <MAC address removed>
[   80.300683] wlan0: send auth to <MAC address removed> (try 1/3)
[   80.337518] wlan0: authenticated
[   80.340469] wlan0: associate with <MAC address removed> (try 1/3)
[   80.385712] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[   80.385821] wlan0: associated
[  157.556630] wlan0: Connection to AP <MAC address removed> lost
[  158.865002] wlan0: authenticate with <MAC address removed>
[  158.884160] wlan0: send auth to <MAC address removed> (try 1/3)
[  158.923697] wlan0: authenticated
[  158.927714] wlan0: associate with <MAC address removed> (try 1/3)
[  158.942752] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  158.942858] wlan0: associated
[  266.185962] wlan0: Connection to AP <MAC address removed> lost
[  267.487176] wlan0: authenticate with <MAC address removed>
[  267.506432] wlan0: send auth to <MAC address removed> (try 1/3)
[  267.515322] wlan0: authenticated
[  267.518194] wlan0: associate with <MAC address removed> (try 1/3)
[  267.561298] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  267.561405] wlan0: associated


########## wireless info END ############

```

Is modprobe the thing I need? What am I modprobing?

Thanks for your guidance.

---

