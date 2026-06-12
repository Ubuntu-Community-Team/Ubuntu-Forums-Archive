---
title: "Ubuntu 12.04 can't connect to Wifi network"
date: 2014-07-27
forum: Networking &amp; Wireless
---

### Post by Clive_Sam on 2014-07-27
Hi,
I have Ubuntu 12.04 (alongside Windows 7 on dual boot). Wifi was working until today when all of a sudden the wifi just  doesnt connect. I checked on Windows 7, and wifi connects there. I tried  searching the forums and tried various things (I'm a newbie so I don't  really know what I did. Just copy pasted codes) but I'm still unable to connect to a wifi network.  
I am able to connect to the internet via cable though. 

further info:

output for code rfkill list:
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

Output for code lspci:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
04:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10)
04:00.2 System peripheral: Broadcom Corporation BCM57765/57785 MS Card Reader (rev 10)
04:00.3 System peripheral: Broadcom Corporation BCM57765/57785 xD-Picture Card Reader (rev 10)
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)


```

Output for code iwconfig:

```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

Output for code lsmod:
```
Module                  Size  Used by
bnep                   24107  2 
rfcomm                 74718  0 
parport_pc             32866  0 
ppdev                  17711  0 
binfmt_misc            17508  1 
nls_iso8859_1          12713  1 
wl                   3074978  0 
lib80211               14381  1 wl
brcmsmac              564374  0 
arc4                   12573  2 
uvcvideo               82247  0 
ath3k                  13368  0 
btusb                  28374  0 
ath9k                 162124  0 
nouveau               979931  1 
bluetooth             391726  12 bnep,rfcomm,ath3k,btusb
snd_hda_codec_hdmi     41773  1 
mac80211              623710  2 brcmsmac,ath9k
snd_hda_codec_realtek    57219  1 
ath9k_common           13859  1 ath9k
videobuf2_core         40815  1 uvcvideo
videodev              138562  2 uvcvideo,videobuf2_core
i915                  696769  3 
snd_hda_intel          57134  3 
ath9k_hw              457718  2 ath9k,ath9k_common
snd_hda_codec         194817  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
bcma                   47094  1 brcmsmac
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
ttm                    84837  1 nouveau
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
brcmutil               15618  1 brcmsmac
joydev                 17613  0 
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
drm_kms_helper         53237  2 nouveau,i915
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
drm                   306660  7 nouveau,i915,ttm,drm_kms_helper
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
i2c_algo_bit           13564  2 nouveau,i915
cfg80211              499466  5 wl,brcmsmac,ath9k,mac80211,ath
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               32938  0 
cordic                 12574  1 brcmsmac
mac_hid                13253  0 
snd                    73753  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13890  1 acer_wmi
mei_me                 18468  0 
mxm_wmi                13021  1 nouveau
mei                    78539  1 mei_me
soundcore              12680  1 snd
wmi                    19256  3 nouveau,acer_wmi,mxm_wmi
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lpc_ich                21163  0 
video                  19574  3 nouveau,i915,acer_wmi
psmouse               108767  0 
serio_raw              13413  0 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
sdhci_pci              19072  0 
tg3                   170756  0 
ahci                   30063  3 
sdhci                  43292  1 sdhci_pci
libahci                32118  1 ahci
ptp                    18627  1 tg3
pps_core               19056  1 ptp


```

Output for code sudo lshw -C network:
```
  *-network               
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 94:39:e5:4d:6c:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-26-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f3a00000-f3a0ffff
  *-network
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 20:6a:8a:5e:5e:73
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 duplex=full firmware=sb ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 memory:f3800000-f380ffff memory:f3810000-f381ffff memory:f3850000-f38507ff


```


Output for code iwlist scan:

```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:15:5B:A0:6B
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000402e1401fb
                    Extra: Last beacon: 23224ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030102
                    IE: Unknown: 0706494E49010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD050010910400
                    IE: Unknown: 050400010000


```


Output for code cat /etc/lsb-release; uname -a:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
Linux clive-Aspire-4755 3.11.0-26-generic #45~precise1-Ubuntu SMP Tue Jul 15 04:02:35 UTC 2014 x86_64 x86_64 x86_64 GNU/Linu
```

Output for code lspci -nnk | grep -iA2 net:
```
03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0500]
    Kernel driver in use: tg3


```


Output for code lsusb:
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 064e:d250 Suyin Corp. 


```



My Ubuntu 12.04 is 64bit. When I try to connect to WIFI, it does not get connected. Instead, it asks for credentials again and again. Any help would be greatly appreciated.
Thankyou.

---

### Post by Bucky Ball on 2014-07-27
Have you tried setting it up manually in Network Manager? Click the network icon and 'Edit'. Navigate to the Wireless connection and fill in the details there, in particular the security key, save and reboot. Are you using a static IP address by any chance?

Fairly sure you have the correct driver installed and the card looks like it is working as it should be from your output. Give the manual details route a try and report back. Good luck.

PS: Might not affect things, but make sure you have no ethernet cable in at the same time. Some machines want to default to that and it can confuse the issue of working out the wifi. ;)

---

### Post by Clive_Sam on 2014-07-27
Thanks Bucky Ball. 

The problem is solved now. That's wierd how easy it was. I did as you directed:
1. Clicked on dashboard
2. Searched "Network"
3. Clicked on "Network" icon
4. Clicked on "Wireless"
5. Selected my wifi network and clicked "Forget Network"
6. Wifi switched off. So I switched it on again via the fn keys.
7. Under "Network Name" > chose "Other"
8. Entered Network details 
9. Clicked Connect
10. Wifi Connected.

---

### Post by Clive_Sam on 2014-07-27
One more thing, how do I mark this as solved?

update: ok done :)

---

### Post by Iowan on 2014-07-27
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

(Slow on the keyboard, again...)

---

### Post by Bucky Ball on 2014-07-27
Good news. Enjoy. ;)

---

