---
title: "Broadcom BCM4313: Unable to connect to WiFi in ubuntu 12.04 on lenovo G570"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by avinash.vattigunta on 2014-01-03
I have lenvo G570 Laptop and I just installed Ubuntu 12.04 and trying to connect wifi but i am not.
below codes are i am getting while run commands

```


*************** info trace ***************

***** uname -a *****

Linux Avinash-Ubuntu 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:25:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: atl1c
--
08:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0489:e00d Foxconn / Hon Hai 
Bus 002 Device 003: ID 5986:0292 Acer, Inc 

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

wl                   3074904  0 
cfg80211              526422  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Kiran:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.137
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             202.83.21.12
    DNS:             202.83.20.101
    DNS:             202.83.23.3



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


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

filename:       /lib/modules/3.8.0-35-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-35-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[   10.707522] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.744024] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   10.935877] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[ 1052.369157] ERROR @wl_dev_intvar_get : error (-1)
[ 1052.369169] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 1145.346364] ERROR @wl_dev_intvar_get : error (-1)
[ 1145.346375] ERROR @wl_cfg80211_get_tx_power : error (-1)

****************** done ******************



```

code for lspci

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M]
07:00.0 Ethernet controller: Qualcomm Atheros AR8152 v2.0 Fast Ethernet (rev c1)
08:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)



```

code for iwconfig

```

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.



```


code for lsmod
```

Module                  Size  Used by
bnep                   18399  2 
rfcomm                 47922  0 
parport_pc             28284  0 
ppdev                  17113  0 
joydev                 17613  0 
fglrx                6728820  186 
lib80211_crypt_tkip    17390  0 
wl                   3074904  0 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_conexant    62464  1 
i915                  621477  2 
coretemp               13596  0 
snd_hda_intel          44339  3 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         49597  1 i915
kvm                   456261  0 
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
drm                   287796  3 i915,drm_kms_helper
snd_timer              29989  2 snd_pcm,snd_seq
uvcvideo               82214  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              526422  1 wl
ghash_clmulni_intel    13259  0 
ideapad_laptop         18596  0 
i2c_algo_bit           13564  1 i915
btusb                  22431  0 
videobuf2_core         40815  1 uvcvideo
rts5139               351018  0 
videodev              130172  2 uvcvideo,videobuf2_core
psmouse                97902  0 
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    45974  0 
cryptd                 20530  1 ghash_clmulni_intel
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
soundcore              12680  1 snd
amd_iommu_v2           19227  1 fglrx
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lpc_ich                17144  0 
mac_hid                13253  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
video                  19652  1 i915
sparse_keymap          13890  1 ideapad_laptop
serio_raw              13215  0 
bluetooth             247324  14 bnep,rfcomm,btusb
microcode              23075  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   25879  2 
libahci                31636  1 ahci
atl1c                  46279  0 


```

code for sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: c1
       serial: dc:0e:a1:6a:05:70
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.137 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:e0500000-e053ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: e4:d5:3d:83:00:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:e0400000-e0403fff



```

Code for iwlist scan
```

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 20:AA:4B:C0:69:AA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"Kiran"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 29816ms ago
                    IE: Unknown: 00054B6972616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD740050F204104A0001101044000102103B0001031047001025015400E79B80F276698F7235C34BAB102100074C696E6B73797310230004453930301024000776312E302E30301042000234321054000800060050F20400011011000445393030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.



```

.Please let me know, if more info. is needed. Would greatly appreciate any help.

---

### Post by avinash.vattigunta on 2014-01-03
I believe the Broadcom STA driver is incorrect for your device  14e4:4727. Please get a temporary wired ethernet connection, open a  terminal and do:  sudo -i
apt-get remove --purge bcmwl-kernel-source
apt-get install linux-firmware-nonfree
echo brcmsmac >> /etc/modules
exit
  Reboot and your wireless should be operating correctly.
This Procedure worked for me
I got this data from [http://askubuntu.com/questions/338391/unable-to-establish-wi-fi-connection-on-some-wireless-networks](http://askubuntu.com/questions/338391/unable-to-establish-wi-fi-connection-on-some-wireless-networks)

---

### Post by Bucky Ball on 2014-01-03
That's interesting. You asked a question and answered yourself!

---

### Post by avinash.vattigunta on 2014-01-03
Not Like That first i serached for almost half a day and i thought its good to post the thread 
again i search with different tags and i got up with that link.
so thought its good to post the answer other wise u guys may try for this issue and wasting u r time.so i dont want to waste ur time after i got solution..
I hope u guys dont mind

---

### Post by Bucky Ball on 2014-01-03
Please mark the thread as solved by using the instructions in my signature. That will help others most. And yes, it is forum etiquette for users to post their solutions if they find one. ;)

---

