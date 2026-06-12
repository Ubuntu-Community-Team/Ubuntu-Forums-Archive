---
title: "wifi problem in Dell Inspiron 6400 / Broadcom BCM4311"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by anl2 on 2014-09-17
after installing xubuntu 14.04, i dont have any wifi options. please help!

---

### Post by praseodym on 2014-09-17
Hi,

please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
rfkill list
route -n
cat /etc/resolv.conf
```
Does LAN work?

---

### Post by anl2 on 2014-09-17
I've tried the code and reboot but still doesn't work. I connect to internet with ethernet cable rigth now.

---

### Post by praseodym on 2014-09-17
The outputs will help us helping ;)

---

### Post by anl2 on 2014-09-18
> **praseodym said:**
> The outputs will help us helping ;)

what do you mean with outputs? i am kinda new user of xubuntu, that's why i dont know much. Please help!

---

### Post by praseodym on 2014-09-18
Open the terminal emulator from the menu and run these commands one by one

---

### Post by anl2 on 2014-09-18
> **praseodym said:**
> Open the terminal emulator from the menu and run these commands one by one

I did but it still doesnt work..

---

### Post by praseodym on 2014-09-18
And, what do you think is the problem?! Argh! Show the outputs, otherwise WE can not help!!!

---

### Post by anl2 on 2014-09-18
> **praseodym said:**
> And, what do you think is the problem?! Argh! Show the outputs, otherwise WE can not help!!!

**1-) uname -a **

Linux Xubuntu 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

**2-) lspci -nnk | grep -iA2 net**

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

**3-) lsusb**

Bus 001 Device 004: ID 05ac:12a8 Apple, Inc. 
Bus 001 Device 002: ID 05ac:1303 Apple, Inc. iPod Shuffle 4.Gen
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 005 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**4-) lsmod**

Module                  Size  Used by
nls_iso8859_1          12617  1 
ipheth                 13216  0 
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
bnep                   18895  2 
rfcomm                 53664  12 
ssb_hcd                12749  0 
gpio_ich               13229  0 
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
b44                    31275  0 
coretemp               13195  0 
kvm                   388084  0 
joydev                 17101  0 
serio_raw              13230  0 
snd_hda_codec_idt      48877  1 
radeon               1420570  3 
snd_hda_intel          42730  3 
r852                   17722  0 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
wl                   3999690  0 
sm_common              16772  1 r852
nand                   58760  2 r852,sm_common
snd_hwdep              13272  1 snd_hda_codec
lib80211               14040  1 wl
lpc_ich                16864  0 
ttm                    72698  1 radeon
nand_ecc               13136  1 nand
drm_kms_helper         47182  1 radeon
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
ssb                    51854  2 b44,ssb_hcd
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
nand_bch               13067  1 nand
snd_seq_midi           13132  0 
bch                    17197  1 nand_bch
snd_seq_midi_event     14475  1 snd_seq_midi
nand_ids                8547  1 nand
cfg80211              409394  4 wl,ath,ath9k,mac80211
drm                   244037  5 ttm,drm_kms_helper,radeon
r592                   17711  0 
snd_rawmidi            25135  1 snd_seq_midi
btusb                  27580  0 
mtd                    52813  2 nand,sm_common
mii                    13654  1 b44
bluetooth             342208  22 bnep,btusb,rfcomm
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
memstick               16174  1 r592
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                     60939  16  snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
i2c_algo_bit           13197  1 radeon
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
video                  18903  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
usb_storage            48417  1 
psmouse                91329  0 
firewire_ohci          35529  0 
sdhci_pci              18535  0 
firewire_core          61867  1 firewire_ohci
sdhci                  37779  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
[B]
5-) iwconfig[/B]

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

**6-) ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 00:15:c5:ac:42:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr b6:18:d1:61:47:78  
          inet addr:172.20.10.4  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::b418:d1ff:fe61:4778/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5382 errors:15 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1237262 (1.2 MB)  TX bytes:1014170 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:177742 (177.7 KB)  TX bytes:177742 (177.7 KB)
[B]
7-) rfkill list[/B]

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: n
[B]
8-) route -n[/B]

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.10.1     0.0.0.0         UG    0      0        0 eth1
172.20.10.0     0.0.0.0         255.255.255.240 U     1      0        0 eth1
[B]
9-) cat /etc/resolv.conf[/B]

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

---

### Post by praseodym on 2014-09-18
Its a Broadcom device, not Atheros.
```

sudo modprobe -rfv ath9k #unloads the wrong one
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
Install the missing firmware for the Broadcom device.:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot and check:
```

lsmod
dmesg | grep b43
iwconfig
cat /etc/modules
```

---

### Post by anl2 on 2014-09-18
> **praseodym said:**
> Its a Broadcom device, not Atheros.
```

sudo modprobe -rfv ath9k #unloads the wrong one
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
Install the missing firmware for the Broadcom device.:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot and check:
```

lsmod
dmesg | grep b43
iwconfig
cat /etc/modules
```

when i tried "sudo apt-get remove --purge bcmwl-kernel-source", 

It says "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem"



i tried manually "sudo dpkg --configure -a" 

and then did what you said but still not working.

**1-) lsmod**

Module                  Size  Used by
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
bnep                   18895  2 
rfcomm                 53664  12 
ipheth                 13216  0 
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
usb_storage            48417  0 
gpio_ich               13229  0 
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
coretemp               13195  0 
kvm                   388084  0 
snd_hda_codec_idt      48877  1 
joydev                 17101  0 
serio_raw              13230  0 
snd_hda_intel          42730  3 
r852                   17722  0 
sm_common              16772  1 r852
nand                   58760  2 r852,sm_common
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
ssb_hcd                12749  0 
snd_hwdep              13272  1 snd_hda_codec
lpc_ich                16864  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
nand_ecc               13136  1 nand
nand_bch               13067  1 nand
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
bch                    17197  1 nand_bch
snd_rawmidi            25135  1 snd_seq_midi
r592                   17711  0 
nand_ids                8547  1 nand
mtd                    52813  2 nand,sm_common
memstick               16174  1 r592
btusb                  27580  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
radeon               1420570  3 
bluetooth             342208  22 bnep,btusb,rfcomm
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
ttm                    72698  1 radeon
parport_pc             31981  0 
drm_kms_helper         47182  1 radeon
ppdev                  17391  0 
snd                    60939  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
mac_hid                13037  0 
drm                   244037  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
video                  18903  0 
soundcore              12600  1 snd
b44                    31275  0 
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
psmouse                91329  0 
ssb                    51854  2 b44,ssb_hcd
sdhci_pci              18535  0 
sdhci                  37779  1 sdhci_pci
mii                    13654  1 b44
crc_itu_t              12627  1 firewire_core

**2-) dmesg | grep b43 **

nothing 

anilayik@Xubuntu:~$ dmesg | grep b43

**3-) iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

**4-) cat /etc/modules**

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp

---

### Post by arun-3 on 2014-09-18
It may be due to some wifi driver problem check this link [https://www.kernel.org/](https://www.kernel.org/) all linux drivers available in this link.

---

### Post by anl2 on 2014-09-18
> **arun-3 said:**
> It may be due to some wifi driver problem check this link [https://www.kernel.org/](https://www.kernel.org/) all linux drivers available in this link.

i've downloaded it, what should i do next?

---

### Post by praseodym on 2014-09-18
Please check if this file is installed:

```
sudo apt-get install linux-image-extra-3.13.0-35-generic
```
Run afterwards:
```

sudo modprobe -rfv ath9k
sudo modprobe -v b43
```

---

### Post by anl2 on 2014-09-18
> **praseodym said:**
> Please check if this file is installed:

```
sudo apt-get install linux-image-extra-3.13.0-35-generic
```
Run afterwards:
```

sudo modprobe -rfv ath9k
sudo modprobe -v b43
```

it worked! thank you very much! :)

---

### Post by praseodym on 2014-09-18
Install the following metapackage:
```

sudo apt-get install linux-generic
```
This will install the file automatically with kernel upgrades

---

