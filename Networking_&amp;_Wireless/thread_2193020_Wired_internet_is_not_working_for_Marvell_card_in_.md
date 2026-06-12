---
title: "Wired internet is not working for Marvell card in Toshiba Satellite"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by MajinSaha on 2013-12-10
Hello!
My wired internet hasn't worked for over several years now and I haven't done anything about it until recently. My laptop is 5 years old, Ubuntu version is 12.04 LTS, 3.2.0-31-generic-pae. The wireless has worked fine. There were no flashes in the Ethernet outlet at all with the active cable plugged, which means the driver itself did not work properly.
So at first, I decided to revive the device by downloading the latest driver from Marvell website for my 88E8040T card, that is "Kernel 2.6.x Linux Driver Install Package for Yukon Devices". I followed the instructions on installation, executed sudo ./install in their InstallDriver directory that the zip package came with. Right after the installation I could see the flashes! Finally. But the internet connection could not be established. The internet sign at the top right corner was constantly indicating that it tried to connect, and I saw occasional "Wired connection 1 disconnected" warning.
Also, the driver stops having its effect after reboot, so I have to rerun driver installation to see the flashes in the outlet again.
Typing 
```
modprobe sk98lin
```
does not help.

Can anyone help me resolve this problem with wired connection?
Just in case, here is my output:
```
saha@saha-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780MC [Mobility Radeon HD 3100 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
06:00.0 Network controller: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) (rev 01)
09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```
and
```

saha@saha-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff  
          inet6 addr: fe80::fdff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:194362 (194.3 KB)  TX bytes:27637 (27.6 KB)
          Interrupt:43 Memory:f0400000-0 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3318370 (3.3 MB)  TX bytes:3318370 (3.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:2b:69:f1  
          inet addr:10.200.48.251  Bcast:10.200.63.255  Mask:255.255.224.0
          inet6 addr: fe80::221:63ff:fe2b:69f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6238277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3667016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3887995105 (3.8 GB)  TX bytes:1010309526 (1.0 GB)

```

---

### Post by varunendra on 2013-12-12
Are you sure the driver was installed without errors? Its link?

And please show us the outputs of -
```
sudo lshw -C network -numeric
lsmod
```

---

### Post by MajinSaha on 2013-12-12
Thanks for your reply!
The link to the driver is here: [http://www.marvell.com/support/downloads/driverSearchResults.do;jsessionid=fSqdSpgH64PwLJGnsRJTL9S2c8T9Lpvg8gHGR2tjbNQzv2Kskfz6!-1730479504](http://www.marvell.com/support/downloads/driverSearchResults.do;jsessionid=fSqdSpgH64PwLJGnsRJTL9S2c8T9Lpvg8gHGR2tjbNQzv2Kskfz6!-1730479504)
Please choose 88E8040 in the drop-down list "Part number". The first in the list is 'Kernel 2.6.x Linux Driver Install Package for Yukon Devices", and that's the one I chose.
This is the output for the first command:
```
  *-network               
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller [11AB:4355]
       vendor: Marvell Technology Group Ltd. [11AB]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: ff:ff:ff:ff:ff:ff
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sk98lin driverversion=10.93.3.3 (03) duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0400000-f0403fff ioport:a000(size=256)
  *-network
       description: Wireless interface
       product: AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) [168C:24]
       vendor: Atheros Communications Inc. [168C]
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:63:2b:69:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-31-generic-pae firmware=N/A ip=10.200.48.251 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:ce000000-ce00ffff

```
and for the second:
```
Module                  Size  Used by
sk98lin               175788  1 
snd_hrtimer            12648  1 
joydev                 17393  0 
snd_hda_codec_conexant    52554  1 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
bluetooth             158438  10 rfcomm,bnep
psmouse                86421  0 
ppdev                  12849  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 117326  0 
serio_raw              13027  0 
mac80211              436455  1 ath9k
k10temp                12990  0 
snd                    62064  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
uvcvideo               67203  0 
radeon                737820  3 
videodev               86588  1 uvcvideo
ath9k_common           13781  1 ath9k
ath9k_hw              391554  2 ath9k,ath9k_common
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
i2c_algo_bit           13199  1 radeon
i2c_piix4              13093  0 
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
shpchp                 32325  0 
wmi                    18744  1 toshiba_acpi
video                  19068  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
pata_atiixp            12999  0 

```

---

### Post by varunendra on 2013-12-12
Please also post the outputs of -
```
nm-tool
modinfo sk98lin
modprobe -c | grep -i 11AB.*4355
```

---

### Post by MajinSaha on 2013-12-12
For the first:
```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sk98lin
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        FF:FF:FF:FF:FF:FF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0  [tamulink-wpa] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        00:21:63:2B:69:F1

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    tamulink-guest:  Infra, 00:0B:85:99:3D:4E, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    eduroam:         Infra, 00:0B:85:99:3D:49, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2 Enterprise
    tamulink-guest:  Infra, 00:0B:85:99:95:AE, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    tamulink-wpa:    Infra, 00:0B:85:99:95:AC, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2 Enterprise
    eduroam:         Infra, 00:0B:85:99:4D:C9, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2 Enterprise
    tamulink-guest:  Infra, 00:0B:85:99:4D:CE, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    tamulink-wpa:    Infra, 00:0B:85:99:4D:CC, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2 Enterprise
    eduroam:         Infra, 00:0B:85:99:4D:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2 Enterprise
    eduroam:         Infra, 00:0B:85:99:95:A9, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2 Enterprise
    tamulink-guest:  Infra, 00:0B:85:99:4E:8E, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    tamulink-wpa:    Infra, 00:0B:85:99:4D:8C, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2 Enterprise
    tamulink-guest:  Infra, 00:0B:85:99:4D:8E, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    eduroam:         Infra, 00:0B:85:99:4E:89, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2 Enterprise
    tamulink-wpa:    Infra, 00:0B:85:99:4E:8C, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2 Enterprise
    tamulink-wpa:    Infra, 00:0B:85:99:3A:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 Enterprise
    eduroam:         Infra, 00:0B:85:99:3A:F9, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise
    tamulink-wpa:    Infra, 00:0B:85:97:2F:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    tamulink-wpa:    Infra, 00:0B:85:97:35:BC, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2 Enterprise
    *tamulink-wpa:   Infra, 00:0B:85:99:3D:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 81 WPA WPA2 Enterprise
    eduroam:         Infra, 00:0B:85:97:35:B9, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2 Enterprise
    tamulink-wpa:    Infra, 00:0B:85:99:4E:6C, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2 Enterprise
    tamulink-guest:  Infra, 00:0B:85:99:4E:6E, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    eduroam:         Infra, 00:0B:85:99:4E:69, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2 Enterprise
    tamulink-guest:  Infra, 00:0B:85:99:3A:FE, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    HPN911a.5387A3:  Ad-Hoc, 02:2A:FA:33:72:33, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    eduroam:         Infra, 00:0B:85:97:2F:F9, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2 Enterprise
    tamulink-guest:  Infra, 00:0B:85:97:2F:FE, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    tamulink-guest:  Infra, 00:0B:85:99:2F:FE, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    tamulink-wpa:    Infra, 00:0B:85:99:2F:FC, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2 Enterprise

  IPv4 Settings:
    Address:         10.200.48.251
    Prefix:          19 (255.255.224.0)
    Gateway:         10.200.32.1

    DNS:             10.200.32.1
    DNS:             128.194.254.1
    DNS:             128.194.254.2
    DNS:             128.194.254.3



```
For the second:
```
filename:       /lib/modules/3.2.0-31-generic-pae/kernel/drivers/net/ethernet/marvell/sk98lin.ko
version:        10.93.3.3
license:        GPL
description:    Marvell/SysKonnect Yukon Ethernet Network Driver
author:         Mirko Lindner <support@marvell.com>
srcversion:     B6855C93810A36F7A9088B6
alias:          pci:v000011ABd00005005sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004382sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004381sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004380sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004370sv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Dsv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Csv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Bsv*sd*bc*sc*i*
alias:          pci:v000011ABd00004369sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004368sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004367sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004366sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004365sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004364sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004363sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004362sv*sd*bc*sc*i*
alias:          pci:v000011ABd0000435Asv*sd*bc*sc*i*
alias:          pci:v000011ABd00004357sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004356sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004355sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004354sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004353sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004352sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004350sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004347sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004346sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004345sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004344sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004343sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004342sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004341sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004340sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004320sv*sd*bc*sc*i*
alias:          pci:v00001186d00004C00sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B03sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B02sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B01sv*sd*bc*sc*i*
alias:          pci:v00001186d00004001sv*sd*bc*sc*i*
alias:          pci:v00001148d00009E01sv*sd*bc*sc*i*
alias:          pci:v00001148d00009E00sv*sd*bc*sc*i*
alias:          pci:v00001148d00009000sv*sd*bc*sc*i*
alias:          pci:v00001148d00004320sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-31-generic-pae SMP mod_unload modversions 686 
parm:           Speed_A:array of charp
parm:           Speed_B:array of charp
parm:           AutoNeg_A:array of charp
parm:           AutoNeg_B:array of charp
parm:           DupCap_A:array of charp
parm:           DupCap_B:array of charp
parm:           FlowCtrl_A:array of charp
parm:           FlowCtrl_B:array of charp
parm:           Role_A:array of charp
parm:           Role_B:array of charp
parm:           ConType:array of charp
parm:           WolType:array of charp
parm:           IntsPerSec:array of int
parm:           Moderation:array of charp
parm:           ModerationMask:array of charp
parm:           LowLatency:array of charp
parm:           TxModeration:array of int
parm:           MsiIrq:array of charp
parm:           RSS:array of charp

```
For the third:
```
alias pci:v000011ABd00004355sv*sd*bc*sc*i* sky2
alias pci:v000011ABd00004355sv*sd*bc*sc*i* sk98lin

```
Maybe I should have mentioned earlier, but the internet access is provided by my university at my office. The cable gives good internet once plugged to the university provided desktop computer. I understand that there might be some defence against connecting to non-university machines, but I thought that in that case the connection must be established at the very least and then the internet access may be blocked once I start browsing.

---

### Post by varunendra on 2013-12-12
Have you manually been editing your device's hardware address to this ? -
```
HW Address:        FF:FF:FF:FF:FF:FF
```

Because if you didn't edit it in your posts, or aren't somehow 'spoofing' it at the system level, this can be indicative of a corrupt or problematic firmware in the card. Although there can be several other reasons for this and accordingly, several fixes, reinstalling the driver (or correct driver) being one of them.

By the way, "sky2" (the native driver) should be more updated than the one you have downloaded. For now, please try these (one at a time, stop where and if any of these seems to make it work, report back) -

1) Try resetting your laptop's BIOS

2) Try these commands -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 **10.200.48.[COLOR="#0000FF"]100[/COLOR]**
```
the IP address above is just for an example. Replace it with a valid, available IP for the network you are trying to connect to, if required.

3) If the above doesn't help -
```
sudo modprobe -rv sk98lin
sudo modprobe -v sky2
```
..then the suggestion in point 2 above if can't automatically pick up an IP address.

4) If still can't connect, check your hardware address (using "nm-tool" or "ifconfig" command) again. Is it still FF:FF:FF:FF:FF:FF ? If yes, please try -
```
sudo ifconfig eth0 hw ether **a0:b0:56:c0:00:00**
```
(the **a0:b0:56:c0:00:00** is a randomly imagined number, which seems more valid than ff:ff:ff:ff:ff:ff :P)
..then the suggestion if point 2 above if can't get the address automatically. Oh, and also check the output of "ifconfig" again to make sure it accepted the above custom MAC address.

Please try these and report back the result.

PS:
I may not be available most of the time today, but shall reply as soon as I get time to.

---

### Post by MajinSaha on 2013-12-13
No, I haven't edited my posts, they are just copy-pasted from the terminal screen. 
Just to be clear, if I try to reset BIOS, is this something I should do during boot process? Do you mean reverting all the settings to the default ones?
Also, since sky2 is more updated, where should I download it from in the future?
Your help is very valuable, I really appreciate all the time you spend answering my posts, even if you can't do it regularly. You seem to know the subject really well.

---

### Post by varunendra on 2013-12-14
> **MajinSaha said:**
> if I try to reset BIOS, is this something I should do during boot process?
Yes, immediately after powering on the laptop, and before the booting of the OS begins.

Usually it is one of the following keys which you need to keep tapping after powering on the laptop until the BIOS setup screen (or a menu to access it) appears on the screen : Esc, Tab, F1, F2, F8 to F12.

Once you are in the BIOS setup, there should be an option to reset it to factory defaults or something to a similar meaning. Usually this option can be located in the last tab of the BIOS setup (Exit tab).

> Do you mean reverting all the settings to the default ones?
Yes I do. But you don't need to do that manually. Just choose the option to "Load Factory Defaults" or "Load Optimized Defaults" (or whatever similar option it is listed in your BIOS as). It will automatically do that in correct manner.

What it will do is to flush all the custom settings or any stuck code in the BIOS memory, and start fresh. Usually it is the 'stuck code' (firmware error) which can cause such issues you are having, and there is no other way to fix that.

"Starting fresh" doesn't mean that you'll have to re-install the OS or something like that. It is just the laptop's firmware that will be refreshed; everything in the hard disk will remain there.

> Also, since sky2 is more updated, where should I download it from in the future?
It is part of the kernel, you don't need to install it from elsewhere. New kernel = new driver.

Newer is not always better, but these native drivers get more attention from the developers than the old proprietary ones (those are coded and uploaded once, then are very rarely updated to address issues that may arise with newer kernels).

Above all, don't let this long explanation give you the false impression that it is a guaranty or even a 'strong' chance of fixing the problem. It is just one of many different possibilities, all of which can have long explanations. Resetting the BIOS is the quickest and easiest thing to try, that's why I suggested it first. :)

---

### Post by MajinSaha on 2013-12-14
Resetting BIOS did not help.
For 2), I have to ask my system administrator, because I certainly don't know the correct IP address of what I'm trying to connect to. So this'll have to wait until the weekend is over. I can't skip 2) and move on to next points, can I?

---

### Post by varunendra on 2013-12-14
Yes you can skip point 2. But I picked up the example IP from the valid IP that was assigned to your wireless interface. If the wireless connects to the same network, you already have the pattern of the IP, just try the example IP as it is, or try replacing the last '100' with randomly chosen other numbers (251 is already assigned to your wireless interface).

If you have other computers around that are connected via cable, you can also confirm the IP pattern by looking at their IP.

If the IP you try is actually available, you will get connected (unless the problem is elsewhere). If it is already being used by another device that is currently active, you won't connect. Nothing worse is going to happen, so you can safely try random numbers on a valid pattern. :)

---

### Post by MajinSaha on 2013-12-15
I did all your points.
2) I tried both 
```
sudo ifconfig eth0 down
sudo ifconfig eth0 10.200.48.100
```
and
```

sudo ifonfig eth0 down
sudo ifconfig eth0 165.91.119.145
``` and nothing changed.
The last address is the one I found by typing "ifconfig eth0" in the other linux machine to which I plugged the same cable.
3) When I typed "sudo modprobe -rv sk98lin", the output was "FATAL: Module sk98lin is in use.", but I proceeded with other commands anyway. I tried both combinations of 2) in the end. Nothing changed.
4) I checked the hardware address, it still was ff:ff:...
Then I typed your suggested command, and after "ifconfig eth0" I saw the hardware address you suggested, i.e. a0:b0:56:c0:00:00. Point 2) provided no connection though.

By the way, I remember installing my Ubuntu about two years ago, and I still had no cable connection there, there were no flashes.

---

### Post by varunendra on 2013-12-15
> **MajinSaha said:**
> The last address is the one I found by typing "ifconfig eth0" in the other linux machine to which I plugged the same cable.
You should try a slightly different address. The same address won't work as long as it is being used by some other device on the network. With some routers, it won't work even if the other device to which it was originally assigned is disconnected (only a few minutes ago), as they tend to remember and expect the same MAC address as well.

> 3) When I typed "sudo modprobe -rv sk98lin", the output was "FATAL: Module sk98lin is in use.", but I proceeded with other commands anyway. I tried both combinations of 2) in the end. Nothing changed.
3 won't work if the first command failed. To do it otherwise, you can blacklist the sk98lin driver to permanently prevent it from loading automatically -
```
echo "blacklist sk98lin" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and check -
```
lsmod | egrep 'sk98|sky'
```
You should only see sky2 driver in the output, not sk98lin. If even sky2 isn't listed, load it manually -
```
sudo modprobe -v sky2
```
..and check lsmod again to confirm it got loaded. Once it is sky2 in use, try all other options I suggested with that one again.

Oh, and **please confirm this also** - When it is (only) sky2 driver in use, do you get a more sensible MAC (HWaddr) address in ifconfig? If not, I highly suspect a corrupt card or firmware, since you have already tried resetting the BIOS. In that case, probably an Ethernet to USB adapter is your only hope.

---

### Post by MajinSaha on 2013-12-17
I repeated the procedure with another IP address: I added 1 or 2 to the last three digist of the address I obtained earlier: 165.91.119.146 or 165.91.119.147. Nothing changed.
Then, I blacklisted sk98lin as you suggested. Then I rebooted. I remind you that my sk98lin driver has to be reinstalled each time I reboot, even "modprobe sk98lin" alone does not load it. But this time I did not reinstall it. I executed 
```
lsmod | egrep 'sk98|sky'
```
and the output was
```
sky2                   53628  0 
```
All this time, there had been no flashes in the outlet since reboot, which means the driver was not active ( if it was there at all ).
Then I tried old options:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 165.91.119.146

```
The output was
```
SIOCSIFFLAGS: Cannot assign requested address

```
Loading driver via
```
sudo modprobe -v sky2
```
did not help remove this message.
However, this error message disappeared after I assigned a hardware address
```
sudo ifconfig eth0 hw ether a0:b0:56:c0:00:00
```
 and tried those commands again.
I saw flashes appear in the outlet and the system try to connect to the internet. This is the first time I see the adapter returning back to life without reinstalling a sk98lin driver from scratch! The connection did not manage to be established though, as before...

---

### Post by varunendra on 2013-12-18
So with either drivers, the HWaddr remanis the same (ff:ff:ff:ff:ff:ff)?

If so, I'm inclined to believe it is a broken card, but let's see the outputs of (with driver sky2 loaded, and HWaddr assigned) -
```
sudo mii-tool
```

Or much better, install 'ethtool' while being connected to internet via wifi -
```
sudo apt-get install ethtool
```
..and post back its output -
```
sudo ethtool eth0
```

---

### Post by MajinSaha on 2013-12-19
To make it clear for you, this is my log after the fresh boot:
```
saha@saha-laptop:~$ sudo ifconfig eth0
[sudo] password for saha: 
eth0      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

saha@saha-laptop:~$ sudo modprobe -v sky2
saha@saha-laptop:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

saha@saha-laptop:~$ sudo ifconfig eth0 hw ether a0:b0:56:c0:00:00
saha@saha-laptop:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr a0:b0:56:c0:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

saha@saha-laptop:~$ sudo modprobe -v sky2
saha@saha-laptop:~$ sudo ifconfig eth0 down
saha@saha-laptop:~$ sudo ifconfig eth0 165.91.119.146

```
Only after the last command I saw flashes ( so it takes both hw ether and IP address to make adapter try to connect ).
Then I typed
```
saha@saha-laptop:~$ sudo ifconfig eth0 down
``` to shut it off.
Only after that, I generated the output you requested:
```
saha@saha-laptop:~$ sudo mii-tool
eth0: negotiated 100baseTx-FD, link ok

```
After the installation of ethtool, I got
```
saha@saha-laptop:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: yes

```

---

### Post by varunendra on 2013-12-19
When it has accepted both HWaddr and IP, please try -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```
If this fails to bring it up, please also try "speed 10".

There are two interrupts related parameters available with the driver that you may use ("disable_msi" and "legacy_pme", both of them accept values "1" (on) or "0" (off)), sometimes they can do the magic. For example, to try parameter "disable_msi", do this -
```
sudo modprobe -rv sky2
sudo modprobe -v sky2 disable_msi=1
```
This will be a temporary change that will be lost at next boot (or a driver unload --> reload cycle, without parameter). If it seems to help, it can be made permanent.

Please keep in mind that the IPs you are trying is just a guess. Even if everything else is good, it won't work if such an IP is assigned that is already in use. Besides, I have no idea which of the combinations of the fixes are required. If it is the interrupt call error, the above parameters should fix it and nothing else should be needed.

To be sure, just try some combinations of the fixes (only parameters first, then with the manually assigned HWaddr/IP) and report back what you tried, and we may look into some further options if possible.

---

### Post by MajinSaha on 2013-12-21
I tried what you said.
The first command did not do anything. However, the command with speed 10 makes it even worse, the connection is no longer seen in the list of the available connections. So I returned to speed 100.
Then I played with interruptions.
Trying ```
sudo modprobe -rv sky2
sudo modprobe -v sky2 XXX
```
alone (where XXX is one of the 4 variants: disable_msi=0, disable_msi=1, legacy_pme=0, legacy_pme=1) does not make the adapter try to connect. Apparently it needs hardware and IP address.
So I did 4 successions of the following commands:
```
sudo modprobe -rv sky2
sudo modprobe -v sky2 XXX
sudo ifconfig eth0 hw ether a0:b0:56:c0:00:00
sudo ifconfig eth0 YYY
```
Here XXX is one of the 4 variants: disable_msi=0, disable_msi=1, legacy_pme=0, legacy_pme=1.
YYY was one of 4-5 IP addresses I tried within each succession, with last 3 digits ranging from 144 to 149.
The output after driver removal was
```
rmmod /lib/modules/3.2.0-57-generic-pae/kernel/drivers/net/ethernet/marvell/sky2.ko
```
The output after driver loading was
```
insmod /lib/modules/3.2.0-57-generic-pae/kernel/drivers/net/ethernet/marvell/sky2.ko XXX
```
Nothing change in my connections. It tries to connect forever, as before, and posts "Wired connection 1 disconnected" every few minutes.
I was lazy typing ```
sudo ifconfig eth0 down
``` before assigning new IP address. Was that important to do?
I think changing IP address does not really affect the way it tries to connect, only the first command matters after hardware address assignment. This is because the way it tries to connect on the top right corner of the screen is not correlated with what IP address I type and when I type it after the previous one ( 30 seconds or 1 minute later ). This is only my observation and is not necessarily true.

---

### Post by varunendra on 2013-12-22
> **MajinSaha said:**
> 
I was lazy typing ```
sudo ifconfig eth0 down
``` before assigning new IP address. Was that important to do?

No it is not. The IP address needs to be assigned only once and as long as it sticks across different other operations you do on the interface, it is not required again. Of course it must be a correct and available IP on the network, not one which is already in use or 'reserved for' another device on the network.

Whatever we have gotten from the interface so far as a response still indicates it may be a broken card or firmware. As a last attempt to get something that confirms it is NOT broken, you can take a look at syslog when it 'tries' to connect.

The moment its light flashes and it seems to be trying to connect, please run this command -
```
tail -40f /var/log/syslog
```
The output will show last 40 lines from /var/log/syslog file, and keep watching it for any further messages. Watch it for a few seconds or a couple of minutes (if the new messages seem to be network related), then press Ctrl-Z to stop the monitoring and post back the entire output here. It may give us some clue to confirm where the remaining problem is.

One more thing - In an attempt to test windows driver on the card, you may try HBCD ([Hiren's Boot CD]("http://www.hirensbootcd.org/download/")) which includes WinXP-PE (Pre-Installed Environment of Windows XP). It offers a very limited functionality of Windows XP in live environment and has a lot of inbuilt network drivers. You get a "Start Networking" wizard icon on its desktop which tries to load correct driver for your card and establish a connection using DHCP (if dhcp is enabled on your network). You can also add your own windows xp drivers to its live environment but that shouldn't be needed for this card.

If even windows drivers fail to activate and use this card, it is almost certainly broken. The windows command to check IP and MAC addresses is "ipconfig", although I'm not sure if it is available or not on HBCD. If even there the MAC address is the same ff:ff:ff:ff:ff:ff, I have no further suggestions other than discarding this port and using an Ethernet-to-USB adapter.

---

### Post by MajinSaha on 2013-12-23
The output for your command was:
```
Dec 23 13:11:02 saha-laptop NetworkManager[826]: <info> Policy set 'tamulink-wpa' (wlan0) as default for IPv4 routing and DNS.
Dec 23 13:11:03 saha-laptop kernel: [54338.775257] sky2 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control rx
Dec 23 13:11:03 saha-laptop kernel: [54338.776107] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 23 13:11:03 saha-laptop NetworkManager[826]: <info> (eth0): carrier now ON (device state 30)
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Auto-activating connection 'Wired connection 1'.
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) starting connection 'Wired connection 1'
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 23 13:11:05 saha-laptop dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> dhclient started with pid 20822
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Beginning IP6 addrconf.
Dec 23 13:11:05 saha-laptop dhclient: Copyright 2004-2011 Internet Systems Consortium.
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 23 13:11:05 saha-laptop dhclient: All rights reserved.
Dec 23 13:11:05 saha-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 23 13:11:05 saha-laptop dhclient: 
Dec 23 13:11:05 saha-laptop NetworkManager[826]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 23 13:11:05 saha-laptop dhclient: Listening on LPF/eth0/a0:b0:56:c0:00:00
Dec 23 13:11:05 saha-laptop dhclient: Sending on   LPF/eth0/a0:b0:56:c0:00:00
Dec 23 13:11:05 saha-laptop dhclient: Sending on   Socket/fallback
Dec 23 13:11:05 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 23 13:11:08 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec 23 13:11:13 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 23 13:11:15 saha-laptop kernel: [54350.568069] eth0: no IPv6 routers present
Dec 23 13:11:21 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 23 13:11:25 saha-laptop NetworkManager[826]: <info> (eth0): IP6 addrconf timed out or failed.
Dec 23 13:11:25 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 23 13:11:25 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 23 13:11:25 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 23 13:11:36 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <warn> (eth0): DHCPv4 request timed out.
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> (eth0): canceled DHCP transaction, DHCP client pid 20822
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <warn> Activation (eth0) failed.
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> (eth0): deactivating device (reason 'none') [0]
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> (eth0): taking down device.
Dec 23 13:11:50 saha-laptop kernel: [54385.207250] sky2 0000:02:00.0: eth0: disabling interface
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <warn> (eth0): failed to change interface MAC address
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <warn> (eth0): failed to reset MAC address to FF:FF:FF:FF:FF:FF
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> (eth0): bringing up device.
Dec 23 13:11:50 saha-laptop kernel: [54385.213981] sky2 0000:02:00.0: eth0: enabling interface
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> (eth0): carrier now OFF (device state 30, deferring action for 4 seconds)
Dec 23 13:11:50 saha-laptop kernel: [54385.216892] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> Policy set 'tamulink-wpa' (wlan0) as default for IPv4 routing and DNS.
Dec 23 13:11:50 saha-laptop NetworkManager[826]: <info> Policy set 'tamulink-wpa' (wlan0) as default for IPv4 routing and DNS.
Dec 23 13:11:51 saha-laptop kernel: [54386.682926] sky2 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control rx
Dec 23 13:11:51 saha-laptop kernel: [54386.683697] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 23 13:11:51 saha-laptop NetworkManager[826]: <info> (eth0): carrier now ON (device state 30)
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Auto-activating connection 'Wired connection 1'.
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) starting connection 'Wired connection 1'
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> dhclient started with pid 20827
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Beginning IP6 addrconf.
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 23 13:11:53 saha-laptop dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Dec 23 13:11:53 saha-laptop dhclient: Copyright 2004-2011 Internet Systems Consortium.
Dec 23 13:11:53 saha-laptop dhclient: All rights reserved.
Dec 23 13:11:53 saha-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 23 13:11:53 saha-laptop dhclient: 
Dec 23 13:11:53 saha-laptop NetworkManager[826]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 23 13:11:53 saha-laptop dhclient: Listening on LPF/eth0/a0:b0:56:c0:00:00
Dec 23 13:11:53 saha-laptop dhclient: Sending on   LPF/eth0/a0:b0:56:c0:00:00
Dec 23 13:11:53 saha-laptop dhclient: Sending on   Socket/fallback
Dec 23 13:11:53 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 23 13:11:56 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 23 13:12:00 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 23 13:12:03 saha-laptop kernel: [54398.784052] eth0: no IPv6 routers present
Dec 23 13:12:10 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Dec 23 13:12:13 saha-laptop NetworkManager[826]: <info> (eth0): IP6 addrconf timed out or failed.
Dec 23 13:12:13 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 23 13:12:13 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 23 13:12:13 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 23 13:12:24 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Dec 23 13:12:33 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <warn> (eth0): DHCPv4 request timed out.
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> (eth0): canceled DHCP transaction, DHCP client pid 20827
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <warn> Activation (eth0) failed.
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> (eth0): deactivating device (reason 'none') [0]
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> (eth0): taking down device.
Dec 23 13:12:38 saha-laptop kernel: [54433.213931] sky2 0000:02:00.0: eth0: disabling interface
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <warn> (eth0): failed to change interface MAC address
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <warn> (eth0): failed to reset MAC address to FF:FF:FF:FF:FF:FF
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> (eth0): bringing up device.
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> (eth0): carrier now OFF (device state 30, deferring action for 4 seconds)
Dec 23 13:12:38 saha-laptop kernel: [54433.221049] sky2 0000:02:00.0: eth0: enabling interface
Dec 23 13:12:38 saha-laptop kernel: [54433.222308] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> Policy set 'tamulink-wpa' (wlan0) as default for IPv4 routing and DNS.
Dec 23 13:12:38 saha-laptop NetworkManager[826]: <info> Policy set 'tamulink-wpa' (wlan0) as default for IPv4 routing and DNS.
Dec 23 13:12:39 saha-laptop kernel: [54434.773774] sky2 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control rx
Dec 23 13:12:39 saha-laptop kernel: [54434.774544] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 23 13:12:39 saha-laptop NetworkManager[826]: <info> (eth0): carrier now ON (device state 30)
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Auto-activating connection 'Wired connection 1'.
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) starting connection 'Wired connection 1'
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> dhclient started with pid 20829
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Beginning IP6 addrconf.
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 23 13:12:41 saha-laptop dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Dec 23 13:12:41 saha-laptop dhclient: Copyright 2004-2011 Internet Systems Consortium.
Dec 23 13:12:41 saha-laptop dhclient: All rights reserved.
Dec 23 13:12:41 saha-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 23 13:12:41 saha-laptop dhclient: 
Dec 23 13:12:41 saha-laptop NetworkManager[826]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 23 13:12:41 saha-laptop dhclient: Listening on LPF/eth0/a0:b0:56:c0:00:00
Dec 23 13:12:41 saha-laptop dhclient: Sending on   LPF/eth0/a0:b0:56:c0:00:00
Dec 23 13:12:41 saha-laptop dhclient: Sending on   Socket/fallback
Dec 23 13:12:41 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 23 13:12:44 saha-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 23 13:12:44 saha-laptop wpa_supplicant[895]: WPA: Group rekeying completed with 00:0b:85:99:3d:4c [GTK=CCMP]
^Z
[1]+  Stopped                 tail -40f /var/log/syslog

```
There are two internet cables in my office, one plugged to the university provided computer and the other being the one I'm currently struggling with. I checked the ip address of the first cable on the first machine, and it is 165.91.119.145, despite the fact that it was absolutely the same address when I tried the second cable a few days ago on the same computer. Can both outlets have the same ip address assigned to them? I'm really not familiar with how this ip-internet stuff works, I'm just using it.
I will try to use HBCD within next few days and will let you know how it goes.
So, since we may end up with broken firmware, I'm curious what I could have done so it broke?
By the way, how does firmware differ from either software or hardware? I get it it's somewhere in between, but what is it precisely? It's actually the first time I hear such word.

---

### Post by varunendra on 2013-12-26
> **MajinSaha said:**
> There are two internet cables in my office, one plugged to the university provided computer and the other being the one I'm currently struggling with. I checked the ip address of the first cable on the first machine, and it is 165.91.119.145, **despite the fact that it was absolutely the same address when I tried the second cable a few days ago on the same computer**. Can both outlets have the same ip address assigned to them?
This indicates one of three reasons -
**1)** Your other computer has been given a permanent IP address manually in the computer itself. In that case, its IP will remain always the same until changed manually.
**2) It has been getting a 'fixed' IP from the router through DHCP (in the router). DHCP can be configured to always assign the same IP to a particular machine which it identifies by its MAC address.**
**3)** The DHCP lease had not expired when you checked the IP again with the second cable. Even though it was a different cable, it was connected to the same router (or DHCP server) which had granted that particular IP to that particular computer (or in other words, to that particular MAC address).

If you really checked the cable a 'few days' ago and this 'few days' means more than 48 hrs., the 3rd possibility is highly unlikely, because generally DHCP leases don't last more than 2-3 days (although it can be configured to last as long as desired).

My guess is that the university router or dhcp server may have been configured to not connect to any machine which it does not recognize. This is specially done in some office setups. If so, no external computer will be able to connect via those extra cables (by default). In that case, you can make your troublesome computer mimic the same MAC address (HWaddr) as the one which is easily getting connected. Of course you will have to disconnect that one when you try to connect the one we are trying to troubleshoot.

So as a test, note down the MAC address of the second computer which has a working connection, then disconnect it. Using the same "sudo ifconfig.." command, assign the same MAC address to your computer, then connect it to the same cable which was connected to the second computer. If that gets you connected, it is the university's networking policy that is preventing it from getting connected (by not accepting an unknown MAC address).

However, the weird ff:ff:.... address with multiple drivers is a strong indication of a fault at either the driver or the card level and so the chance of success with above experiment is very little.

> So, since we may end up with broken firmware, I'm curious what I could have done so it broke?
While it can be any of the other reasons like a buggy card, wearing out of electronic components, some physical damage or system crash during its operation, the most common cause of such faults is some abnormal power supply or power surge on the card. Most of the logical chips are highly sensitive to power ratings and can't stand even half volts higher than they are supposed to get.

That being said, the firmware is just a special kind of software, and it can get corrupted due to any reason which can corrupt a normal software, most often - accidentally.

> By the way, how does firmware differ from either software or hardware? I get it it's somewhere in between, but what is it precisely? It's actually the first time I hear such word.
From [Wikipedia]("http://en.wikipedia.org/wiki/Firmware") -
> In electronic systems and computing, firmware is the combination of persistent memory and program code and data stored in it.
In a very generalized form, it is a miniature Operating System software which controls the device.

Normal OS and Software are usually installed by the user as per their needs, can be very versatile, and they work on a varying set of data generally supplied by the user.

In contrast, the firmware is embedded in the device (or in some cases, loaded in the device just before it becomes operational), does some very specific job (of controlling the device), and works with a fixed set of data which is also stored as a part of it.

Hope this gives a rough difference between the OS, Software and firmware. :)

---

### Post by MajinSaha on 2013-12-26
Please see my post below.

---

### Post by MajinSaha on 2013-12-26
Wow! I almost lost all hope and was ready to accept the fact that my firmware was broken. This advice here
> **varunendra said:**
> So as a test, note down the MAC address of the second computer which has a working connection, then disconnect it. Using the same "sudo ifconfig.." command, assign the same MAC address to your computer, then connect it to the same cable which was connected to the second computer. If that gets you connected, it is the university's networking policy that is preventing it from getting connected (by not accepting an unknown MAC address).
worked like magic! I'm writing this post using this new cable connection on my laptop! I intentionally disconnected from my wireless to test new connection! Thanks, you're a wizard!
So, it seems my card is not broken after all?
How can I make this change permanent?
I have to type
```

sudo modprobe -v sky2
sudo ifconfig eth0 hw ether 00:22:19:ff:2f:ee
sudo ifconfig eth0 165.91.119.145

```
every time to get connected ( well, maybe without the first command ).
So it seems it was university's policy that didn't let me connect. And now I broke that policy. I'm not even sure if that's bad or not.
My logical questions would be: when I use other cables in the future, what MAC address should I assign to my laptop? It seems this trick here worked specifically with the MAC address from another machine that was connected before ( your previous MAC address did nothing, as you may remember ), but I may not have such resources in the future and would like to be independent of other machines.
And I guess I won't need to test anything with HBCD?

---

### Post by varunendra on 2013-12-28
> **MajinSaha said:**
> So, it seems my card is not broken after all?
Not as badly as I initially suspected, but the awkward MAC address is an indication that not everything is fine either. But as long as it works with a manually assigned IP, it is at least usable.

> How can I make this change permanent?
I have to type
```

sudo modprobe -v sky2
sudo ifconfig eth0 hw ether 00:22:19:ff:2f:ee
sudo ifconfig eth0 165.91.119.145

```
Assuming you are using Network Manager, save this MAC address (00:22:19:ff:2f:ee) in the "Cloned MAC address" field of your wired connection settings. On next boot, it should automatically assign this address to your card. Use "ifconfig" command to confirm that. And yes, the first (modprobe..) command is unnecessary.

> So it seems it was university's policy that didn't let me connect. And now I broke that policy. I'm not even sure if that's bad or not.
..and I helped you breaking the policy, certainly not the right thing from a wider perspective, but let me save myself by saying I just provided help to make sure the card itself is functional and the problem was external. :P

> My logical questions would be: when I use other cables in the future, what MAC address should I assign to my laptop? It seems this trick here worked specifically with the MAC address from another machine that was connected before ( your previous MAC address did nothing, as you may remember ), but I may not have such resources in the future and would like to be independent of other machines.
Unless the other networks too impose MAC based restrictions, any imaginary MAC address would do, including the one I proposed earlier. But if such restrictions are in effect, there is no other way in my knowledge other than 'Spoofing' an address that the router/firewall is allowed to connect to.

> And I guess I won't need to test anything with HBCD?
Well.. you can still do the experiment to test whether the card gets a valid MAC address with windows drivers or not. If not, it means the card is indeed broken in some way (hardware or firmware), although it is usable.

---

### Post by MajinSaha on 2013-12-30
> Assuming you are using Network Manager, save this MAC address (00:22:19:ff:2f:ee) in the "Cloned MAC address" field of your wired connection settings. On next boot, it should automatically assign this address to your card. Use "ifconfig" command to confirm that. And yes, the first (modprobe..) command is unnecessary.

Not sure what you mean by Network Manager, but I went to "Edit connections..." at the top right corner of the screen. When I chose my Wired connection 1 and clicked Edit..., I saw a mentioned field "Cloned MAC address", but it didn't let me save the MAC I typed in, the Save button was inactive. I tried both lower and upper case letters for e and f in the address.

I guess this discussion is about to end, so the question above is not really crucial, but if you know how to work around this little issue, that would be helpful. Maybe with command line and sudo?

If I find time, I'll try to check my card with HBCD, but it's not likely I'll post any comments here on that. I guess I'll mark this thread as SOLVED after your next post.
Thanks for your help, this was awesome and really professional of you! At least now I know what to start playing with when I need to get me a cable internet. Have a nice day!

---

### Post by varunendra on 2014-01-01
Thanks for your kind comments and sorry for not being able to respond quickly.

> **MajinSaha said:**
> Not sure what you mean by Network Manager, but I went to "Edit connections..." at the top right corner of the screen. When I chose my Wired connection 1 and clicked Edit..., I saw a mentioned field "Cloned MAC address", but it didn't let me save the MAC I typed in, the Save button was inactive. I tried both lower and upper case letters for e and f in the address.
The Network Manager is the name of the program that provides that menu you used, so you are indeed using it.

But not being able to save the settings is something unusual. I simply copy-pasted the MAC id from my previous post into an existing connection and the 'Save' option was active for me. The only reasons I can think of are :

1) a typo (for example, incomplete id, or a blank space before or in-between the address "00:22:19:ff:2f:ee"). In this case, the "Save" button will become inactive as soon as you make the typo, otherwise it will stay active.

2) Permissions issue. Means you are not authorized to edit that connection. In this case, the "Save" button will stay inactive from the beginning, even when you haven't made any changes. If you are able to create new connections, you can simply delete and recreate this one (or create a new one) to overcome this problem.

The second type of problem above shouldn't arise if you are the only (and first) user on the Ubuntu installation on that laptop. So the first reason is more probable.

> if you know how to work around this little issue, that would be helpful. Maybe with command line and sudo?
Sure. You can 'force add' this line -
```
cloned-mac-address=00:22:19:FF:2F:EE
```
under the "[802-3-ethernet]" section in your 'KeyFile' for the connection. 

The keyfile is the file that stores all the critical information about connections. It is located in **/etc/NetworkManager/system-connections** directory and its name is usually (maybe always) the same as the connection name (by which it appears in the drop-down menu of nm-applet which you clicked). It is a privileged file and can be read or edited only by root.

You can open the file with gksu or sudo as follows -
```
gksu gedit /etc/NetworkManager/system-connections/MyConnection1
```
..then add the line under the relevant section. The name "MyConnection1" is just an example and "gedit" the text editor (will be different for different Desktop Environments).

The contents of an example file with the above "Cloned MAC address" is -
```


[802-3-ethernet]
duplex=full
**[COLOR="#FF0000"]cloned-mac-address=00:22:19:FF:2F:EE[/COLOR]**

[connection]
id=My Connection 1
uuid=*<some alpha-numeric characters>*
type=802-3-ethernet
timestamp=128882020

[ipv6]
method=ignore

[ipv4]
method=auto
```

You can also use the /etc/network/interfaces file to spoof the MAC id and ignore Network Manager altogether, but that is not recommended unless you are really comfortable with the 'interfaces' file and the methods related to it.

---

### Post by MajinSaha on 2014-01-03
I re-checked: there was no typo and no spaces in the field. I'd have attached a screenshot of how it looks, but this forum only allows to attach pictures from URLs.
And what really surprised me is the fact there was no file "Wired connection 1" in /etc/NetworkManager/system-connections. All I saw was files of different wireless connections that my laptop experienced connecting to at various times.
So I decided to create it with sudo. I followed your pattern ( for alpha-numerical characters of uuid I just typed several random digits ). Then I replugged the cable ( didn't reboot though. Did I have to? ). Nothing changed in the window of the Network Manager.

---

### Post by varunendra on 2014-01-03
> **MajinSaha said:**
> And what really surprised me is the fact there was no file "Wired connection 1" in /etc/NetworkManager/system-connections. All I saw was files of different wireless connections that my laptop experienced connecting to at various times..

I'm not very sure but I guess it is so because the connection was never created by Network Manager. We established it with the help of command "ifconfig" which is independent of Network Manager.

Instead of directly creating the keyfile, try creating a dummy wired connection (by any name) from Network Manager itself (nm-applet drop-down menu > "Edit Connections..." > "Add"). It should create the key-file with a valid UUID and the rest of fields in it. While creating the connection, use the "Cloned MAC address" trick. Does it allow creating a connection that way?

If not, I wonder if you have required privileges on that installation. To verify that, please post the outputs of -
```
id
ls -la /etc/NetworkManager/system-connections
```

Funny how I'm enjoying this thread despite having little to no success.. :)

---

### Post by MajinSaha on 2014-01-06
I created a new connection "Dummy" and erased the previous one. I typed in "Cloned MAC address" and saved, but I noticed it didn't let me save once I started typing in the "Device MAC address" field, so I left it blank. Same thing was happening with the "Wired connection 1" ( before I deleted it ), the Save button became active once I removed the contents of the "Device MAC address" field.
After reboot, I saw no signs of improvement. I, again, had to assign both the new MAC and IP addresses from the command line to make "Dummy" connect.
The output you requested:
```
uid=1000(saha) gid=1000(saha) groups=1000(saha),4(adm),20(dialout),24(cdrom),46(plugdev),116(lpadmin),118(admin),124(sambashare)

```
and
```
total 108
drwxr-xr-x 2 root root 4096 Jan  6 16:28 .
drwxr-xr-x 6 root root 4096 Dec 17 10:35 ..
-rw------- 1 root root  303 Nov 29 07:45 Ag Swag
-rw------- 1 root root  222 Nov 26 20:08 Ag Swag-guest
-rw------- 1 root root  210 Nov 26 16:10 attwifi
-rw------- 1 root root  234 Nov 30 20:38 Austin & Jake-guest
-rw------- 1 root root  231 Dec  8 09:36 Belkin_G_Wireless_
-rw------- 1 root root  349 Dec 13 18:23 BitchDon'tKillMyVibe
-rw------- 1 root root  348 Sep 10  2012 CAES-AUSSOIS
-rw------- 1 root root  213 Jan  6 16:28 Dummy
-rw------- 1 root root  210 Nov 23  2012 FON_MTS
-rw------- 1 root root  344 Dec  1 09:30 HTC Portable Hotspot
-rw------- 1 root root  210 Jul  9  2012 libfree
-rw------- 1 root root  233 Dec  8 09:32 linksys
-rw------- 1 root root  351 Oct 31  2012 Livebox-c13a
-rw------- 1 root root  334 Oct 28  2012 Livebox-c13a 1
-rw------- 1 root root  320 Jul 12  2012 NAMDEMUN
-rw------- 1 root root  233 Dec 29 10:45 NETGEAR
-rw------- 1 root root  309 Dec  3 20:56 Plochistan
-rw------- 1 root root  225 Nov 26 20:49 print server 372A0F
-rw------- 1 root root  327 Nov 27 21:52 suddenlink.net-AFCE
-rw------- 1 root root  209 Dec  7 09:33 TheZone
-rw------- 1 root root  212 Jun 27  2012 TRENDnet
-rw------- 1 root root  218 Jun 27  2012 TRENDnet652
-rw------- 1 root root  309 Jul  9  2012 VGBIL_Free
-rw------- 1 root root  220 Aug 28  2012 WIFI-ADM-UM2
-rw------- 1 root root  220 Nov 22  2012 WIFI-AIRPORT

```

---

### Post by varunendra on 2014-01-06
> **MajinSaha said:**
> I typed in "Cloned MAC address" and saved, but I noticed it didn't let me save once I started typing in the "Device MAC address" field, so I left it blank.
What were you typing in the "Device MAC address"? It is only meant for 'binding' the connection with one of your network interfaces (so that connection can only be established using that particular interface). It should offer you to choose from a drop-down list of detected (wired) interfaces.

Also, the "Save" button remains inactive only until the address is correctly completed (it can't let you save an incomplete address). So the behaviour you mentioned sounds normal to me, but.... -

We finally seem to have some more clue, unless the following is a copy-paste mistake -
> **MajinSaha said:**
> ```
uid=1000(saha) gid=1000(saha) groups=1000(saha),4(adm),[COLOR="#FF0000"]????[/COLOR],20(dialout),24(cdrom),[COLOR="#FF0000"]????[/COLOR],[COLOR="#FF0000"]????[/COLOR],46(plugdev),116(lpadmin),118(admin),124(sambashare)

```
Where is [COLOR="#FF0000"]disk[/COLOR]? Where is [COLOR="#FF0000"]**sudo**[/COLOR]? Where is [COLOR="#FF0000"]**dip**[/COLOR]?

You not being a member of 'disk' group may be normal, but not being a member of 'dip' group is a bit suspicious, and not being a member of '**sudo**' group is certainly mysterious, unless the above is a copy-paste mistake.

If the above is correct and full output of 'id' command, then either I need to learn a lot more about Linux user groups, or there is something seriously wrong with permissions on your system. I wonder how you have been able to run the commands with 'sudo' when you are not a member of that group. I'd like to see the output of -
```
sudo cat /etc/sudoers
```

And I don't remember if I proposed it earlier, but can you try a Live CD/DVD/USB to see if all is well there?

---

### Post by MajinSaha on 2014-01-08
I'll try to respond more fully soon, but for now:
the output from the last command is
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```
and for command "id", the output is the one I got the second time. There is no typo, as well as no "disk", "sudo" and "dip".

---

### Post by varunendra on 2014-01-08
> **MajinSaha said:**
> ..There is no typo, as well as no "disk", "sudo" and "dip".

Please try adding yourself to these groups -
```
sudo adduser saha sudo
sudo adduser saha dip
sudo adduser saha disk
```

Then reboot and see if you can use the MAC id in the new connections you create. I'm guessing that you are not able to use a MAC address (thus preventing 'you' to use a local network device) because of not being in 'dip' user group. You are able to use automatically created connections because those are created by system services automatically (hence by 'root') and are configured to 'Allow Everyone' to use them.

Anyway, this is just a guess and I'm not sure if that is going to make any change. But can you try a Live CD/USB to see if the interface gets a HWaddr automatically there? Or if you can save the MAC addresses newly created 'Demo' connections in the Live sesssion? If yes, I recommend doing a fresh install unless you are willing to try various cumbersome 'patches' to do something as simple as spoofing an address, which should be very easy on a healthy installation.

---

### Post by MajinSaha on 2014-01-10
> **varunendra said:**
> What were you typing in the "Device MAC address"? It is only meant for 'binding' the connection with one of your network interfaces (so that connection can only be established using that particular interface). It should offer you to choose from a drop-down list of detected (wired) interfaces.
The first thing I did after reboot is assign the MAC address, but no IP address yet. Then I went to "Edit connections...", to "Dummy". There I tried to type some device MAC address. When I inserted the cloned MAC address into the "Device MAC address" field, the "Save" button became active. It's active only until I erase the last two digits ("EE") and leave it as "00:22:19:FF:2F:". Even with only one "E" at the end the button is still active. The button is always inactive when I put "FF:FF:FF:FF:FF:FF" inside or any part of it. By the way, the original device MAC address for deleted "Wired connection 1" was "FF:FF:FF:FF:FF:FF (eth0)", which is why probably it didn't let me save.
> And I don't remember if I proposed it earlier, but can you try a Live CD/DVD/USB to see if all is well there?
Not at the moment. Can we avoid this way, at least for now? I currently don't have enough time to download Ubuntu and make it bootable from USB. Too much hassle.

---

### Post by MajinSaha on 2014-01-10
I executed those "adduser" three times successfully. After reboot, I did not see any significant change. There was "Wired connection 1" again in the list of wired connections, but none of "Dummy" or "Wired connection 1" tried to connect until I forcefully assigned mac address and ip address. I remind you that before reboot the "Device MAC address" field of "Dummy" was empty, and only "Cloned" one was filled. Should I interchange those two and try to reboot again?

So, it is necessary to try Live boot. Ok, I'll try to find some time and do it. I'll keep you updated.

---

### Post by MajinSaha on 2014-01-10
Just an immediate update. The computer administrator guy came to my office and warned me not to use the cable anymore on my laptop. So I guess those tricks with cloned MAC id need to stop unless I get me a home cable. But that should be soon, as I'm moving to a new apartment with provided internet ( in a couple of weeks ).
But I guess we still can try to experiment during weekends, when none of the administrators are around. After all, I'm sure my computer is free of viruses (it's linux after all) and I'm not trying to damage the network or anything, so why not?

---

### Post by MajinSaha on 2014-02-09
Bump, please.

varunendra, sorry for not writing to you earlier.
About two weeks ago I moved into a new apartment with a provided cable internet. What I did there was:
1) assigned MAC address as I did previously: 
```
sudo ifconfig eth0 hw ether 00:22:19:ff:2f:ee
```
2) assigned arbitrary, but existing IP address. I took the address from another country!
```
sudo ifconfig eth0 xx.xx.xx.xx
```
The internet works.
So, as a concluding word, I'm not gonna use my laptop for ethernet connection anywhere except when at home. When I use it at home, each time after reboot I have to enter these two commands in the terminal. After three years of no ethernet at all, than't not a pretty bad deal, if you think about it.
Thank you for your help. I wouldn't have obtained the internet if you hadn't been doing all those experiments described above. Although I understand the behavior we were witnessing still seems confusing to you.
I wish you all the best. Bye!

---

### Post by varunendra on 2014-02-09
Aha.. glad to see it still works. :)

I was about to reply to your last post when I got too indulged in some personal tasks here, almost forgot this one later..

> Although I understand the behavior we were witnessing still seems confusing to you.
Yup, confusing it is to some extent. But an advancement in my learning experience nonetheless.., and I thank You for your willingness to cooperate and try whatever I suggested even if they didn't make much sense at some point.

If you are satisfied with what we have in hand right now, then I think you should consider marking the thread as [SOLVED] now, so others with same/similar problem and looking for help can notice that this one may have a working solution/workaround for them.

But if you want to experiment further, I'd only be glad to help, as much as I can. I'm not sure I have much left in my stock of suggestions, but I'd love to dig deeper as and if the time allows.

See you around ! :)

---

### Post by MajinSaha on 2014-02-09
I'd be glad to learn myself, but I don't have so much time for that right now. So I guess it's solved for now. When I feel like it, I will make a new thread in the future where I describe what I currently have as a starting point. 
Best wishes! :)

---

