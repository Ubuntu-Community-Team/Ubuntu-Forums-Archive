---
title: "ATHEROS AR9285 + UBUNTU 13.10 + connexion really slow"
date: 2014-03-04
forum: Networking &amp; Wireless
---

### Post by Jeremy971 on 2014-03-04
Hello, I installed Ubuntu on my laptop toshiba Qosmio F750 and I've a really slow connexion with my wifi.

Here my ping :

packets transmitted     9
received     0
packet loss     100 %
time     8055 ms

I tried to fix the problem with this code line but it doesn't work :

```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```

Any to idea to fix it ? 

```

 cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"

    lsusb

Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 2488:0000  
Bus 001 Device 003: ID 04f2:b26a Chicony Electronics Co., Ltd 
Bus 001 Device 007: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

    lspci

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
02:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07)
02:00.1 System peripheral: Ricoh Co Ltd Device e232 (rev 04)
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

    lspci -nn | grep -i net

03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)

    lspci -k

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Toshiba America Info Systems Device 0001
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
	Kernel driver in use: pcieport
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: mei_me
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
	Kernel driver in use: pcieport
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
	Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: ahci
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: nouveau
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
	Kernel driver in use: snd_hda_intel
02:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: sdhci-pci
02:00.1 System peripheral: Ricoh Co Ltd Device e232 (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Lite-On Communications Inc Device 6613
	Kernel driver in use: ath9k
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
	Subsystem: Toshiba America Info Systems Device 0003
	Kernel driver in use: r8169
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: xhci_hcd

    sudo lshw -C network

 *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:a2:4f:af
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-17-generic firmware=N/A ip=10.241.208.119 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:c3300000-c330ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: e8:9d:87:e1:6a:2c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:2000(size=256) memory:c3104000-c3104fff memory:c3100000-c3103fff

    lsmod

Module                  Size  Used by
dm_crypt               22832  1 
ath3k                  13318  0 
btusb                  28267  0 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
snd_hda_codec_hdmi     41117  4 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
arc4                   12608  2 
snd_hda_codec_realtek    56405  1 
snd_hda_intel          52267  12 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ath9k                 155779  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_hwdep              13602  1 snd_hda_codec
uvcvideo               80885  0 
snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aesni_intel            55624  781 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
ath9k_common           13859  1 ath9k
videobuf2_core         40499  1 uvcvideo
snd_rawmidi            30095  1 snd_seq_midi
ath9k_hw              444732  2 ath9k_common,ath9k
videodev              133509  2 uvcvideo,videobuf2_core
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              597268  1 ath9k
ablk_helper            13597  1 aesni_intel
joydev                 17377  0 
snd_timer              29433  2 snd_pcm,snd_seq
cryptd                 20359  392 ghash_clmulni_intel,aesni_intel,ablk_helper
mei_me                 18421  0 
mei                    77782  1 mei_me
cfg80211              480503  3 ath,ath9k,mac80211
snd                    69141  34 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
lpc_ich                21080  0 
toshiba_acpi           22901  0 
toshiba_bluetooth      12852  0 
sparse_keymap          13948  1 toshiba_acpi
psmouse                97655  0 
mac_hid                13205  0 
serio_raw              13413  0 
microcode              23656  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
bluetooth             372041  23 bnep,ath3k,btusb,rfcomm
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  2 hid_generic,usbhid
usb_storage            62062  1 
nouveau               943717  3 
mxm_wmi                13021  1 nouveau
wmi                    19070  3 toshiba_acpi,mxm_wmi,nouveau
i2c_algo_bit           13413  1 nouveau
ttm                    84169  1 nouveau
drm_kms_helper         52710  1 nouveau
ahci                   25819  2 
drm                   297056  5 ttm,drm_kms_helper,nouveau
sdhci_pci              19014  0 
r8169                  67581  0 
libahci                32009  1 ahci
sdhci                  42898  1 sdhci_pci
mii                    13934  1 r8169
video                  19318  1 nouveau

    iwconfig

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 0C:27:24:47:DE:54   
          Bit Rate=9 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:806   Missed beacon:0

    ifconfig

eth0      Link encap:Ethernet  HWaddr e8:9d:87:e1:6a:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101056 (101.0 KB)  TX bytes:101056 (101.0 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:a2:4f:af  
          inet addr:10.241.208.119  Bcast:10.241.255.255  Mask:255.255.0.0
          inet6 addr: fe80::d2df:9aff:fea2:4faf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:110912443 (110.9 MB)  TX bytes:7779555 (7.7 MB)

    sudo iwlist scan

 Cell 17 - Address: 0C:27:24:47:DD:31
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000787ff37a0cf
                    Extra: Last beacon: 948ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B050100738D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 851E03008F000F00FF0359004C454D303257430000000000000000000100003A
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD090040960E010073690F
                    IE: Unknown: DD050040961401
 
    uname -r -m

3.11.0-17-generic x86_64

    cat  /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

    nm-tool


NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E8:9D:87:E1:6A:2C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [eduroam] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        D0:DF:9A:A2:4F:AF

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    eduroam:         Infra, 0C:27:24:47:DD:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2 Enterprise
    connectPro084:   Infra, C8:D3:A3:5C:03:A5, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ulaval-inv:      Infra, 0C:27:24:47:DE:53, Freq 2462 MHz, Rate 54 Mb/s, Strength 90
    ulaval-vpn:      Infra, 0C:27:24:47:DE:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 90
    ulaval-inv:      Infra, 0C:27:24:47:DB:E3, Freq 2412 MHz, Rate 54 Mb/s, Strength 64
    ulaval-inv:      Infra, 64:D8:14:6F:D8:D3, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    ulaval-vpn:      Infra, 0C:27:24:47:DD:32, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    ulaval-vpn:      Infra, 0C:27:24:47:DD:E2, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    ulaval-inv:      Infra, 0C:27:24:47:DD:E3, Freq 2462 MHz, Rate 54 Mb/s, Strength 25
    ulaval-vpn:      Infra, 0C:27:24:47:D8:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    ulaval-inv:      Infra, 0C:D9:96:01:DE:23, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    eduroam:         Infra, 0C:27:24:47:DD:34, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2 Enterprise
    ulaval-vpn:      Infra, 0C:27:24:47:DB:E2, Freq 2412 MHz, Rate 54 Mb/s, Strength 55
    ulaval-inv:      Infra, 0C:27:24:47:DD:33, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    HP-Print-64-LaserJet 1102: Infra, 08:3E:8E:92:9D:64, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    ulaval-inv:      Infra, 64:D8:14:86:F3:33, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    eduroam:         Infra, 0C:27:24:47:D8:84, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2 Enterprise
    eduroam:         Infra, 0C:27:24:47:DB:E4, Freq 2412 MHz, Rate 54 Mb/s, Strength 53 WPA WPA2 Enterprise
    *eduroam:        Infra, 0C:27:24:47:DE:54, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2 Enterprise
    eduroam:         Infra, 0C:D9:96:00:6E:B4, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2 Enterprise
    ulaval-vpn:      Infra, 0C:D9:96:00:6E:B2, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    ulaval-inv:      Infra, 0C:D9:96:00:6E:B3, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    ulaval-inv:      Infra, 0C:27:24:47:D8:83, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    ulaval-vpn:      Infra, 64:D8:14:6F:D8:D2, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    eduroam:         Infra, 0C:D9:96:01:DE:24, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2 Enterprise
    ulaval-vpn:      Infra, 0C:D9:96:01:DE:22, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    ulaval-vpn:      Infra, B4:E9:B0:9F:95:B3, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    ulaval-inv:      Infra, B4:E9:B0:9F:95:B5, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    eduroam:         Infra, 64:D8:14:86:F3:34, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2 Enterprise
    ulaval-vpn:      Infra, 64:D8:14:86:F3:32, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    eduroam:         Infra, 64:D8:14:6F:D8:D4, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2 Enterprise
    eduroam:         Infra, B4:E9:B0:9F:95:B6, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    ulaval-inv:      Infra, 64:D8:14:86:FF:D3, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    ulaval-vpn:      Infra, 70:10:5C:F9:50:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    eduroam:         Infra, 64:D8:14:86:FF:D4, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 Enterprise
    ulaval-inv:      Infra, 70:10:5C:F9:50:B3, Freq 2437 MHz, Rate 54 Mb/s, Strength 19
    HP-Print-38-LaserJet 1102: Infra, E4:D5:3D:B1:6C:38, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    ulaval-vpn:      Infra, 64:D8:14:86:FF:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 20

  IPv4 Settings:
    Address:         10.241.208.119
    Prefix:          16 (255.255.0.0)
    Gateway:         10.241.0.1

    DNS:             10.141.1.10
    DNS:             10.141.129.10

    sudo rfkill list

0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by Jeremy971 on 2014-03-05
up

---

### Post by varunendra on 2014-03-05
Welcome to the forums Jeremy!

Which Access-Point are you having this problem with? The nm-tool output shows you are connected to "eduroam", while the "iwlist scan" output you have quoted is a different access-point.

If it is the one quoted from "iwlist scan", and if it is under your control, there is one thing you should immediately change - the encryption type. Currently it is set to WPA/WPA2 mixed mode with TKIP, you should change it to pure WPA2-PSK with AES, no mixed mode, no TKIP. Save the changes and reboot the router. Regardless of whether it helps or not, keep this setting.

However, if you are experiencing slow speeds with all networks, or if the above alone doesn't help, you may either try a couple more tweaks, or try compiling a newer driver which has been reported to be woking better then the one you currently have (but there is no guarantee that it will certainly work better).

If you wish to try the tweaks, please follow the "Wireless Script" link in my signature below, download and run the script as per instructions there and post back the report it generates.

If you prefer to try the newer driver, please follow the instructions in this post : [http://ubuntuforums.org/showthread.php?t=2205970&p=12932329#post12932329](http://ubuntuforums.org/showthread.php?t=2205970&p=12932329#post12932329)

If it helps, please provide your feedback about the performance. :)

---

### Post by Jeremy971 on 2014-03-05
> 

If it is the one quoted from "iwlist scan", and if it is under your  control, there is one thing you should immediately change - the  encryption type. Currently it is set to WPA/WPA2 mixed mode with TKIP,  you should change it to pure WPA2-PSK with AES, no mixed mode, no TKIP.  Save the changes and reboot the router. Regardless of whether it helps  or not, keep this setting.



I don't think I can change this setting. I've no option in network connections. But i run your script :


```



*************** info trace ***************

***** uname -a *****

Linux jeremy-QOSMIO-F750 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6613]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Toshiba America Info Systems Device [1179:0003]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 003: ID 04f2:b26a Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 2488:0000  
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 004: ID 05ac:1297 Apple, Inc. iPhone 4

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=58.5 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:163   Missed beacon:0


***** rfkill *****

0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****


***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.241.0.1      0.0.0.0         UG    0      0        0 wlan0
10.241.0.0      0.0.0.0         255.255.0.0     U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

***** lsmod *****

ath3k                  13368  0 
bluetooth             391726  25 ath3k,btusb,rfcomm,bnep
ath9k                 161996  0 
mac80211              619465  1 ath9k
ath9k_common           13859  1 ath9k
ath9k_hw              457667  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
cfg80211              499466  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

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


- Device: wlan0  [eduroam] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 Enterprise
    connectPro084:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    ulaval-inv:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72
    ulaval-inv:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    ulaval-inv:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    ulaval-inv:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    ulaval-inv:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    ulaval-inv:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    ulaval-inv:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    ulaval-inv:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    ulaval-inv:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    HP-Print-64-LaserJet 1102: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2 Enterprise
    *eduroam:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2 Enterprise
    ulaval-inv:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2 Enterprise
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    ulaval-inv:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 Enterprise
    ulaval-vpn:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20

  IPv4 Settings:
    Address:         10.241.208.119
    Prefix:          16 (255.255.0.0)
    Gateway:         10.241.0.1

    DNS:             10.141.1.10
    DNS:             10.141.129.10



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000185378f1bc
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0507005F8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"ulaval-vpn"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000185378c470
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D76706E
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E12008F000F00FF0359004C454D3035574B0000000000000000000700003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000185380e026
                    Extra: Last beacon: 276ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0507005F8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E12008F000F00FF0359004C454D3035574B0000000000000000000700003A
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD090040960E07005F690F
                    IE: Unknown: DD050040961401
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"ulaval-inv"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001853799d71
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D696E76
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E12008F000F00FF0359004C454D3035574B0000000000000000000700003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"connectPro084"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001860b2c180
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 000D636F6E6E65637450726F303834
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018535ec55c
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0505006B8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"ulaval-vpn"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000019789e18d2db
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D76706E
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E05008F000F00FF03590041444A303657460000000000000000000400003A
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"ulaval-vpn"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018535e9803
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D76706E
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E05008F000F00FF0359004C454D303557420000000000000000000500003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 09 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018535dd026
                    Extra: Last beacon: 2348ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0505006B8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359004C454D303557420000000000000000000500003A
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD090040960E05006B690F
                    IE: Unknown: DD050040961401
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018537bd834
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B050500518D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000185380e026
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B050500518D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E02008F000F00FF0359004C454D303557470000000000000000000500003A
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD090040960E050051690F
                    IE: Unknown: DD050040961401
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-64-LaserJet 1102"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000016b1d3063a
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 001948502D5072696E742D36342D4C617365724A65742031313032
                    IE: Unknown: 01088C1218243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"ulaval-vpn"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018537bab92
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D76706E
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E02008F000F00FF0359004C454D303557470000000000000000000500003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"ulaval-inv"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018537aec90
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D696E76
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E02008F000F00FF0359004C454D303557470000000000000000000500003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 15 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"ulaval-inv"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000019789e19aed5
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D696E76
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E05008F000F00FF03590041444A303657460000000000000000000400003A
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 16 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000184e660026
                    Extra: Last beacon: 2336ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050700010600800000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0516001C8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1601000F00000000000000000000000000000000000000
                    IE: Unknown: 851E07008F000F00FF0359004C454D303257410000000000000000001600003A
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD090040960E16001C690F
                    IE: Unknown: DD050040961401
          Cell 17 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"ulaval-inv"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018535dd026
                    Extra: Last beacon: 2324ms ago
                    IE: Unknown: 000A756C6176616C2D696E76
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E05008F000F00FF0359004C454D303557420000000000000000000500003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 18 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"ulaval-inv"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009d7ab2716f4
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D696E76
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E06008F000F00FF03590041444A303457410000000000000000000A00003A
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 19 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"ulaval-inv"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001977e792f1ce
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A756C6176616C2D696E76
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E01008F000F00FF03590041444A303657470000000000000000000200003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 20 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"ulaval-vpn"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001977e793c026
                    Extra: Last beacon: 2316ms ago
                    IE: Unknown: 000A756C6176616C2D76706E
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E01008F000F00FF03590041444A303657470000000000000000000200003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 21 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009d7ab268026
                    Extra: Last beacon: 2316ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B050A00278D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 22 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"ulaval-inv"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000184e660026
                    Extra: Last beacon: 2312ms ago
                    IE: Unknown: 000A756C6176616C2D696E76
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050700010600800000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E07008F000F00FF0359004C454D303257410000000000000000001600003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 23 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"ulaval-vpn"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009d7ab268026
                    Extra: Last beacon: 2304ms ago
                    IE: Unknown: 000A756C6176616C2D76706E
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E06008F000F00FF03590041444A303457410000000000000000000A00003A
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 24 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000019789e195026
                    Extra: Last beacon: 2304ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0504002B8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 25 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018536dc04a
                    Extra: Last beacon: 1648ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0504005B8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 26 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"ulaval-inv"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018536a9027
                    Extra: Last beacon: 1648ms ago
                    IE: Unknown: 000A756C6176616C2D696E76
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E16008F000F00FF0359004C454D3035574C0000000000000000000700003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 27 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"ulaval-vpn"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018536dc04a
                    Extra: Last beacon: 1636ms ago
                    IE: Unknown: 000A756C6176616C2D76706E
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E02008F000F00FF0359004C454D303557410000000000000000000400003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 28 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000184e6f9026
                    Extra: Last beacon: 1612ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079218243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050700010640000000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B051700608D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1606000F00000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     247033A5A2EF74BAFEF2634
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9960BB0B644BE14E4A2F42B
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    9.381089] ath: phy0: ASPM enabled: 0x43
[    9.381094] ath: EEPROM regdomain: 0x65
[    9.381096] ath: EEPROM indicates we should expect a direct regpair map
[    9.381098] ath: Country alpha2 being used: 00
[    9.381099] ath: Regpair used: 0x65
[   15.746285] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.746493] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.576864] wlan0: authenticate with <MAC address removed>
[   18.599713] wlan0: send auth to <MAC address removed> (try 1/3)
[   18.603692] wlan0: authenticated
[   18.607781] wlan0: associate with <MAC address removed> (try 1/3)
[   18.614561] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=73)
[   18.614620] wlan0: associated
[   18.614648] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************



```

---

### Post by varunendra on 2014-03-06
I have already posted all the options available to you. Can't help further unless you are descriptive in your posts and answer ALL the questions asked. Please re-read my post to see what answers I was expecting.

By the way, the encryption is something that has to be changed in the router/access-point, not in Network Manager. Of course you can't do that if it is not under your control.

---

