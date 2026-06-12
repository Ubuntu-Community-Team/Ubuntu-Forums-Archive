---
title: "No Wireless, Hard Block on wifi adapter"
date: 2014-11-22
forum: Networking &amp; Wireless
---

### Post by jreedy06 on 2014-11-22
I have updated the bios but still no wifi


here is my script output
```

########## wireless info START ##########

Report from: 22 Nov 2014 20:59 EST -0500

Booted last: 22 Nov 2014 20:58 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: r8169

05:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak] [8086:0087] (rev 5f)
    Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN [8086:1301]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8086:0186 Intel Corp. WiMAX Connection 2400m
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: i2400m-usb:2-4:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
mac80211              626511  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:36:77:c8  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe36:77c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8221169 (8.2 MB)  TX bytes:282831 (282.8 KB)

wlan2     Link encap:Ethernet  HWaddr 64:80:99:25:8b:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmx0      Link encap:Ethernet  HWaddr 64:d4:da:29:31:0d  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################

wmx0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan2     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 192.168.1.1
search home

##### nm-tool ###########################


NetworkManager Tool

State: connected (global)

- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        64:D4:DA:29:31:0D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan2 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        64:80:99:25:8B:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1E:EC:36:77:C8

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]

[ifupdown]

##### NetworkManager profiles ###########



##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

wmx0      no frequency information.

eth0      no frequency information.

lo        no frequency information.

wlan2     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################
```

---

### Post by jreedy06 on 2014-11-22
Oh, Computer is Toshiba Satellite a205-5000

---

### Post by weatherman2 on 2014-11-22
Are you sure the wireless is enabled?  Most laptops have either a physical toggle switch to turn wireless on/off (off saves power say on an airplane) or a function key combo to toggle wireless on/off - Fn+F2 on a Dell for example, Fn+F3 on my Acer.  No idea what it would be on your Toshiba.  I'd at least try toggling the key to see what it does, if anything.

---

### Post by jreedy06 on 2014-11-22
Yes, it is enabled. I have a physical on/off switch that is in the "on" position (that gives me the hard block). I can also turn on and off the wifi with the function key plus F8. This turns off and on the soft block.

---

### Post by praseodym on 2014-11-23
Please show the full output of
```

lsmod
```
Tried to reset the BIOS?

---

### Post by jeremy31 on 2014-11-23
Try ```
sudo modprobe -r i2400m_usb
``````
sudo rfkill unblock all
```
Is this the original wifi for the laptop?

---

### Post by jreedy06 on 2014-11-23
Module                  Size  Used by
btrfs                 835954  0 
raid6_pq               97812  1 btrfs
xor                    21411  1 btrfs
ufs                    74890  0 
msdos                  17332  0 
xfs                   912173  0 
libcrc32c              12644  2 xfs,btrfs
nvram                  14411  0 
i2400m_usb             36521  0 
i2400m                107913  1 i2400m_usb
wimax                  34704  1 i2400m
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  3 
coretemp               13435  0 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
joydev                 17381  0 
serio_raw              13462  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
lpc_ich                21080  0 
snd_rawmidi            30144  1 snd_seq_midi
pcmcia                 62299  0 
arc4                   12608  2 
rfcomm                 69160  4 
tifm_7xx1              13371  0 
bnep                   19624  2 
iwldvm                232285  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
tifm_core              15771  1 tifm_7xx1
bluetooth             395423  10 bnep,rfcomm
mac80211              626511  1 iwldvm
iwlwifi               169932  1 iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
yenta_socket           41027  0 
pcmcia_rsrc            18407  1 yenta_socket
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
pcmcia_core            23592  3 pcmcia,pcmcia_rsrc,yenta_socket
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
soundcore              12680  1 snd
parport_pc             32701  0 
toshiba_acpi           22901  0 
sparse_keymap          13948  1 toshiba_acpi
ppdev                  17671  0 
binfmt_misc            17468  1 
lp                     17759  0 
wmi                    19177  1 toshiba_acpi
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13205  0 
ahci                   25819  1 
psmouse               102222  0 
firewire_ohci          40409  0 
libahci                32168  1 ahci
firewire_core          68769  1 firewire_ohci
i915                  783485  2 
sdhci_pci              23172  0 
sdhci                  43015  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
i2c_algo_bit           13413  1 i915
r8169                  67581  0 
mii                    13934  1 r8169
drm_kms_helper         52758  1 i915
drm                   302817  3 i915,drm_kms_helper
video                  19476  1 i915

---

### Post by praseodym on 2014-11-23
Try unloading this module
```

sudo rmmod toshiba_acpi
sudo rfkill unblock all
```

---

### Post by jreedy06 on 2014-11-23
Here is the result of the "sudo modprobe -r i2400m_usb"

modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.13.0-27-generic/modules.dep.bin'

This is not the original wifi card.

---

### Post by jeremy31 on 2014-11-23
Try ```
echo "blacklist wimax" | sudo tee -a /etc/modprobe.d/blacklist.conf
``` and reboot

---

### Post by jreedy06 on 2014-11-23
No effect after 
sudo rmmod toshiba_acpi
and sudo rfkill unblock all

---

### Post by jeremy31 on 2014-11-23
Any idea how old this laptop is?  Are there any BIOS updates available?  I was able to put my 6250 card in my newer Toshiba(newer than the one the card came with) and it worked.

---

